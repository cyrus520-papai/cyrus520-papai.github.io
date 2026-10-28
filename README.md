import random

class Card:
    def __init__(self, name, card_type, shard_cost, strength=0, chroma_gain=0, achrom_drain=0):
        self.name = name
        self.card_type = card_type       # 'Character', 'Location', 'Object', 'Action'
        self.shard_cost = shard_cost     # Shards spent to deploy
        self.strength = strength         # Combat power
        self.chroma_gain = chroma_gain   # Shards gained at turn end
        self.achrom_drain = achrom_drain # Shards drained from enemy at turn end

class Player:
    def __init__(self, name, deck):
        self.name = name
        self.shards = 10                 # Both players start at 10 Shards
        self.deck = deck
        random.shuffle(self.deck)
        self.hand = [self.deck.pop() for _ in range(4)] # Initial draw
        self.canvas = []                 # Active playing field
        self.dregs = []                  # Discard pile

    def play_card(self, card_name, target_enemy=None):
        card = next((c for c in self.hand if c.name.lower() == card_name.lower()), None)
        if not card:
            print(f"❌ {card_name} is not in your hand.")
            return False
        
        if self.shards < card.shard_cost:
            print(f"❌ Not enough shards! Needs {card.shard_cost}, you have {self.shards}.")
            return False

        self.shards -= card.shard_cost
        self.hand.remove(card)
        
        if card.card_type == 'Action':
            print(f"✨ {self.name} casts Action: {card.name}!")
            if card.achrom_drain > 0 and target_enemy:
                drain = min(target_enemy.shards, card.achrom_drain)
                target_enemy.shards -= drain
                self.shards += drain
                print(f"🩸 Stole {drain} shards from {target_enemy.name}!")
            self.dregs.append(card)
        else:
            print(f"🃏 Deployed {card.card_type}: {card.name} to the Canvas.")
            self.canvas.append(card)
        return True

    def resolve_canvas_phase(self, enemy):
        """End of turn shard modification based on Canvas cards"""
        for card in self.canvas:
            if card.chroma_gain > 0:
                self.shards += card.chroma_gain
                print(f"☀️ {card.name} generated +{card.chroma_gain} Chroma Shards for {self.name}.")
            if card.achrom_drain > 0:
                drain = min(enemy.shards, card.achrom_drain)
                enemy.shards -= drain
                self.shards += drain
                print(f"🔮 {card.name} drained {drain} Achrom Shards from {enemy.name}.")

    def draw_card(self):
        if self.deck:
            card = self.deck.pop()
            self.hand.append(card)
            print(f"📥 {self.name} drew a card.")
        else:
            print(f"⚠️ {self.name}'s Palette (deck) is empty!")

    def show_status(self):
        print(f"\n=== {self.name} | Shards: {self.shards} ===")
        print(f"Canvas: {[c.name for c in self.canvas] if self.canvas else '[Empty]'}")
        print(f"Hand: {[c.name for c in self.hand]}")

# --- Game Setup & Card Definition Pool ---
def create_sample_deck():
    return [
        Card("Curdle Hill Zealot", "Character", shard_cost=2, strength=2, chroma_gain=1),
        Card("Draco Temple Guard", "Character", shard_cost=3, strength=4, chroma_gain=0, achrom_drain=1),
        Card("Flutterby Pixie", "Character", shard_cost=1, strength=1, chroma_gain=2),
        Card("Achromic Surge", "Action", shard_cost=2, achrom_drain=3),
        Card("Wishwell Nexus", "Location", shard_cost=4, chroma_gain=3),
        Card("Scepter of Achrom", "Object", shard_cost=2, achrom_drain=1)
    ]

# --- Quick Simulation Loop ---
player1 = Player("Chroma Nexus", create_sample_deck() + create_sample_deck())
player2 = Player("Achrom Zealot", create_sample_deck() + create_sample_deck())

print("⚔️ ARCHROMA ENGINES ONLINE ⚔️")
turn = 1

while player1.shards > 0 and player2.shards > 0 and player1.shards < 30 and player2.shards < 30:
    print(f"\n--- TURN {turn} ---")
    current_player = player1 if turn % 2 != 0 else player2
    opponent = player2 if turn % 2 != 0 else player1
    
    current_player.show_status()
    
    # Simple automated AI action choice: Play the first affordable card
    playable_cards = [c for c in current_player.hand if c.shard_cost <= current_player.shards]
    if playable_cards:
        chosen_card = playable_cards[0]
        current_player.play_card(chosen_card.name, target_enemy=opponent)
    else:
        print(f"💤 {current_player.name} passes card deployment.")
        
    # End of turn phase
    current_player.resolve_canvas_phase(opponent)
    current_player.draw_card()
    
    # Check Win Conditions
    if current_player.shards >= 30 or opponent.shards <= 0:
        break
        
    turn += 1

print("\n🏆 GAME OVER 🏆")
if player1.shards >= 30 or player2.shards <= 0:
    print(f"🎉 Player 1 ({player1.name}) Wins!")
elif player2.shards >= 30 or player1.shards <= 0:
    print(f"🎉 Player 2 ({player2.name}) Wins!")
