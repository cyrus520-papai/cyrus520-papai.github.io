// ==========================================
// 1. DATA LAYER: data/cards.json
// ==========================================
/*
[
  {
    "id": "1",
    "name": "Achromax, The Unraveler",
    "faction": "Chroma",
    "type": "Character",
    "cost": 5,
    "rarity": "Legendary",
    "rules": "When Achromax enters the battlefield, drain 2 Shards from your opponent.",
    "imageUrl": "https://unsplash.com"
  },
  {
    "id": "2",
    "name": "Shard Burst",
    "faction": "Achros",
    "type": "Action",
    "cost": 2,
    "rarity": "Rare",
    "rules": "Gain 3 temporary Shards this turn.",
    "imageUrl": "https://unsplash.com"
  },
  {
    "id": "3",
    "name": "Crystalline Golem",
    "faction": "Chroma",
    "type": "Character",
    "cost": 3,
    "rarity": "Common",
    "rules": "Prevent the first 1 damage dealt to this character each turn.",
    "imageUrl": "https://unsplash.com"
  }
]
*/

// ==========================================
// 2. MAIN LAYOUT: app/layout.tsx
// ==========================================
import React from 'react';
import './globals.css'; // Contains standard Tailwind directives

export const metadata = {
  title: 'Chroma Nexus | Card Database',
  description: 'Explore the cards, lore, and strategies of the realm.',
};

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en" className="dark">
      <body className="bg-slate-950 text-slate-100 min-h-screen font-sans selection:bg-purple-600 selection:text-white">
        {/* Global Navigation Header */}
        <header className="sticky top-0 z-50 bg-slate-900/80 backdrop-blur-md border-b border-slate-800 px-6 py-4 flex justify-between items-center">
          <div className="flex items-center space-x-3">
            <div className="w-8 h-8 rounded-md bg-gradient-to-tr from-purple-600 to-indigo-500 animate-pulse" />
            <span className="text-xl font-bold tracking-wider uppercase bg-gradient-to-r from-white to-slate-400 bg-clip-text text-transparent">
              CHROMA NEXUS
            </span>
          </div>
          <nav className="hidden md:flex space-x-8 text-sm font-medium tracking-wide">
            <a href="/" className="hover:text-purple-400 transition-colors">Home</a>
            <a href="/cards" className="text-purple-400 border-b-2 border-purple-500 pb-1">Card Database</a>
            <a href="#" className="hover:text-purple-400 transition-colors">Lore Chronicles</a>
            <a href="#" className="hover:text-purple-400 transition-colors">Decks</a>
          </nav>
          <button className="bg-purple-600 hover:bg-purple-700 text-white font-semibold text-xs uppercase px-5 py-2.5 rounded shadow-lg shadow-purple-900/30 transition-all active:scale-95">
            Launch App
          </button>
        </header>

        {/* Dynamic View Wrapper */}
        <main>{children}</main>

        {/* Global Footer */}
        <footer className="border-t border-slate-900 bg-slate-950 text-center py-8 text-sm text-slate-500">
          <p>© {new Date().getFullYear()} Chroma Nexus. Inspired by tactical TCG universes.</p>
        </footer>
      </body>
    </html>
  );
}

// ==========================================
// 3. INTERACTIVE CARD PORTAL: app/cards/page.tsx
// ==========================================
'use client';

import { useState, useMemo } from 'react';

// local placeholder matching data/cards.json structural parameters
const sampleCards = [
  {
    id: "1",
    name: "Achromax, The Unraveler",
    faction: "Chroma",
    type: "Character",
    cost: 5,
    rarity: "Legendary",
    rules: "When Achromax enters the battlefield, drain 2 Shards from your opponent.",
    imageUrl: "https://unsplash.com"
  },
  {
    id: "2",
    name: "Shard Burst",
    faction: "Achros",
    type: "Action",
    cost: 2,
    rarity: "Rare",
    rules: "Gain 3 temporary Shards this turn.",
    imageUrl: "https://unsplash.com"
  },
  {
    id: "3",
    name: "Crystalline Golem",
    faction: "Chroma",
    type: "Character",
    cost: 3,
    rarity: "Common",
    rules: "Prevent the first 1 damage dealt to this character each turn.",
    imageUrl: "https://unsplash.com"
  }
];

export default function CardDatabase() {
  const [search, setSearch] = useState('');
  const [selectedFaction, setSelectedFaction] = useState('All');

  // Client-side execution filtering matrix
  const filteredCards = useMemo(() => {
    return sampleCards.filter((card) => {
      const matchesSearch = card.name.toLowerCase().includes(search.toLowerCase()) ||
                            card.rules.toLowerCase().includes(search.toLowerCase());
      const matchesFaction = selectedFaction === 'All' || card.faction === selectedFaction;
      return matchesSearch && matchesFaction;
    });
  }, [search, selectedFaction]);

  return (
    <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10">
      {/* Dynamic Header Node */}
      <div className="mb-10 text-center md:text-left">
        <h1 className="text-4xl font-extrabold tracking-tight sm:text-5xl bg-gradient-to-r from-purple-400 to-indigo-300 bg-clip-text text-transparent">
          Card Codex
        </h1>
        <p className="mt-2 text-slate-400 max-w-xl">
          Query values, inspect gameplay rules, and filter down specific mechanics across entire regional card expansions instantly.
        </p>
      </div>

      {/* Control Filtering Layer */}
      <div className="bg-slate-900 border border-slate-800 p-6 rounded-xl mb-8 flex flex-col md:flex-row gap-4 items-center justify-between">
        <div className="w-full md:w-1/2">
          <label htmlFor="search" className="block text-xs font-semibold uppercase tracking-wider text-slate-400 mb-2">Search Cards</label>
          <input
            id="search"
            type="text"
            placeholder="Search by card name, keyword or rules text..."
            className="w-full bg-slate-950 border border-slate-700 rounded-lg px-4 py-2.5 text-sm focus:outline-none focus:border-purple-500 focus:ring-1 focus:ring-purple-500 transition"
            value={search}
            onChange={(e) => setSearch(e.target.value)}
          />
        </div>

        <div className="w-full md:w-auto flex flex-col sm:flex-row gap-2 self-end md:self-auto">
          <div className="w-full">
            <span className="block text-xs font-semibold uppercase tracking-wider text-slate-400 mb-2">Faction Alliance</span>
            <div className="inline-flex rounded-lg p-1 bg-slate-950 border border-slate-800">
              {['All', 'Chroma', 'Achros'].map((faction) => (
                <button
                  key={faction}
                  onClick={() => setSelectedFaction(faction)}
                  className={`px-4 py-1.5 rounded-md text-xs font-medium uppercase tracking-wider transition ${
                    selectedFaction === faction
                      ? 'bg-purple-600 text-white shadow'
                      : 'text-slate-400 hover:text-white'
                  }`}
                >
                  {faction}
                </button>
              ))}
            </div>
          </div>
        </div>
      </div>

      {/* UI Result Matrix */}
      {filteredCards.length === 0 ? (
        <div className="text-center py-20 border border-dashed border-slate-800 rounded-xl bg-slate-900/30">
          <p className="text-slate-400">No archival instances match your active layout filtering metrics.</p>
        </div>
      ) : (
        <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
          {filteredCards.map((card) => (
            <div
              key={card.id}
              className="group bg-slate-900 border border-slate-800/80 rounded-xl overflow-hidden hover:border-purple-500/50 shadow-xl transition-all hover:-translate-y-1 duration-300"
            >
              {/* Graphic Render Wrapper */}
              <div className="relative aspect-[3/4] bg-slate-950 w-full overflow-hidden border-b border-slate-800">
                <img
                  src={card.imageUrl}
                  alt={card.name}
                  loading="lazy"
                  className="object-cover w-full h-full transition duration-500 group-hover:scale-105 opacity-80 group-hover:opacity-100"
                />
                {/* Cost Badge Node */}
                <div className="absolute top-3 right-3 w-8 h-8 rounded-full bg-slate-950/90 border border-purple-500 flex items-center justify-center font-bold text-sm text-purple-400 backdrop-blur-sm">
                  {card.cost}
                </div>
                {/* Faction Subtag Overlay */}
                <div className="absolute bottom-2 left-2 px-2 py-0.5 rounded bg-slate-900/90 text-[10px] font-bold tracking-widest uppercase border border-slate-700 backdrop-blur-sm">
                  {card.faction}
                </div>
              </div>

              {/* Text Meta Descriptions Container */}
              <div className="p-4">
                <div className="flex justify-between items-start gap-2 mb-1">
                  <h3 className="font-bold text-base tracking-wide text-white group-hover:text-purple-300 transition-colors line-clamp-1">
                    {card.name}
                  </h3>
                </div>
                <div className="flex gap-2 mb-3 text-[11px] font-medium tracking-wide">
                  <span className="text-slate-400">{card.type}</span>
                  <span className="text-slate-600">•</span>
                  <span className={`
                    ${card.rarity === 'Legendary' ? 'text-amber-400' : ''}
