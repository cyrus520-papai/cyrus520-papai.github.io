


export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body className="bg-slate-950 text-slate-100 min-h-screen font-sans flex flex-col justify-between">
        <header className="border-b border-slate-800 bg-slate-900/80 backdrop-blur sticky top-0 z-50 px-6 py-4">
          <div className="max-w-7xl mx-auto flex justify-between items-center">
            <a href="/" className="text-2xl font-black tracking-widest text-indigo-400 hover:text-indigo-300">
              ACHROMA<span className="text-white">REALM</span>
            </a>
            <nav className="flex space-x-6 text-sm font-medium tracking-wide">
              <a href="/cards" className="hover:text-indigo-400 transition-colors">Card Database</a>
              <a href="/lore" className="hover:text-indigo-400 transition-colors">Lore Archives</a>
              <a href="#" className="hover:text-indigo-400 transition-colors">How to Play</a>
            </nav>
          </div>
        </header>

        <main className="flex-grow">{children}</main>

        <footer className="border-t border-slate-900 bg-black/40 text-center py-6 text-xs text-slate-500">
          &copy; {new Date().getFullYear()} Achroma Realm. Independent developer concept framework.
        </footer>
      </body>
    </html>
  );
}


=== FILE: app/page.tsx ===
import React from 'react';

export default function HomePage() {
  return (
    <div className="relative isolate overflow-hidden">
      {/* Hero Accent Background */}
      <div className="absolute inset-x-0 -top-40 -z-10 transform-gpu overflow-hidden blur-3xl sm:-top-80">
        <div className="relative left-[calc(50%-11rem)] aspect-[1155/678] w-[36rem] -translate-x-1/2 rotate-[30deg] bg-gradient-to-tr from-indigo-500 to-purple-600 opacity-20 sm:left-[calc(50%-30rem)] sm:w-[72rem]"></div>
      </div>

      <div className="max-w-5xl mx-auto px-6 py-24 text-center">
        <span className="inline-flex items-center rounded-full bg-indigo-500/10 px-3 py-1 text-xs font-medium text-indigo-400 ring-1 ring-inset ring-indigo-500/20 mb-4">
          New Expansion Out Now
        </span>
        <h1 className="text-5xl md:text-7xl font-extrabold tracking-tight text-white mb-6">
          Unleash the Power of <span className="text-transparent bg-clip-text bg-gradient-to-r from-indigo-400 to-purple-400">Chromas</span>
        </h1>
        <p className="text-lg md:text-xl text-slate-400 max-w-2xl mx-auto mb-10 leading-relaxed">
          Dive into a stunning tactical card adventure. Track stats, craft your ultimate deck, and explore the shifting timelines of the Achroma universe.
        </p>
        <div className="flex justify-center gap-4">
          <a href="/cards" className="rounded-md bg-indigo-600 px-6 py-3 text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600 transition-all">
            Browse Card Codex
          </a>
          <a href="/lore" className="rounded-md border border-slate-700 bg-slate-900/50 px-6 py-3 text-sm font-semibold hover:bg-slate-800 transition-all">
            Read Chronicles
          </a>
        </div>
      </div>
    </div>
  );
}


=== FILE: data/cards.json ===
[
  {
    "id": "1",
    "name": "Chroma Dragon",
    "faction": "Magus",
    "type": "Character",
    "rarity": "Legendary",
    "cost": 5,
    "text": "When deployed, steal 2 Shards from your opponent.",
    "image": "https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=400&q=80"
  },
  {
    "id": "2",
    "name": "Cursed Relic",
    "faction": "Occult",
    "type": "Object",
    "rarity": "Rare",
    "cost": 2,
    "text": "All characters lose 1 Health at the start of each turn.",
    "image": "https://images.unsplash.com/photo-1519074069444-1ba4aaf7207c?w=400&q=80"
  },
  {
    "id": "3",
    "name": "Paladin Shield",
    "faction": "Spiritual",
    "type": "Action",
    "rarity": "Common",
    "cost": 3,
    "text": "Give targeted ally +3 Armor until the next round.",
    "image": "https://images.unsplash.com/photo-1599733589046-10c005739ef9?w=400&q=80"
  }
]

=== FILE: app/cards/page.tsx ===
'use client';
import React, { useState } from 'react';
import cardData from '../../data/cards.json';

export default function CardsDatabasePage() {
  const [factionFilter, setFactionFilter] = useState('All');
  const [searchQuery, setSearchQuery] = useState('');

  const filteredCards = cardData.filter(card => {
    const matchesFaction = factionFilter === 'All' || card.faction === factionFilter;
    const matchesSearch = card.name.toLowerCase().includes(searchQuery.toLowerCase());
    return matchesFaction && matchesSearch;
  });

  return (
    <div className="max-w-7xl mx-auto px-6 py-12">
      <div className="flex flex-col md:flex-row md:items-center md:justify-between gap-6 pb-8 border-b border-slate-800 mb-10">
        <div>
          <h1 className="text-3xl font-bold tracking-tight text-white">Card Codex</h1>
          <p className="text-slate-400 text-sm mt-1">Filter, examine, and research card attributes in real-time.</p>
        </div>
        <div className="flex flex-wrap gap-3">
          <input 
            type="text" 
            placeholder="Search cards..." 
            value={searchQuery}
            onChange={(e) => setSearchQuery(e.target.value)}
            className="bg-slate-900 border border-slate-700 rounded-md px-4 py-2 text-sm focus:outline-none focus:border-indigo-500 w-64"
          />
          <select 
            value={factionFilter} 
            onChange={(e) => setFactionFilter(e.target.value)}
            className="bg-slate-900 border border-slate-700 rounded-md px-4 py-2 text-sm focus:outline-none focus:border-indigo-500"
          >
            <option value="All">All Factions</option>
            <option value="Magus">Magus</option>
            <option value="Occult">Occult</option>
            <option value="Spiritual">Spiritual</option>
          </select>
        </div>
      </div>

      <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
        {filteredCards.map(card => (
          <div key={card.id} className="group relative rounded-xl border border-slate-800 bg-slate-900/50 p-4 hover:border-slate-700 transition-all flex flex-col justify-between hover:shadow-xl overflow-hidden">
            <div>
              <div className="aspect-square w-full rounded-lg overflow-hidden bg-slate-800 mb-4 relative">
                <img src={card.image} alt={card.name} className="w-full h-full object-cover group-hover:scale-105 transition-transform duration-300"/>
                <div className="absolute top-2 right-2 bg-indigo-600 text-white font-bold text-xs px-2 py-1 rounded-full shadow-md">
                  Cost: {card.cost}
                </div>
              </div>
              <div className="flex items-center justify-between mb-2">
                <span className="text-xs uppercase tracking-wider text-indigo-400 font-semibold">{card.faction}</span>
                <span className="text-xs text-slate-500">{card.type}</span>
              </div>
              <h3 className="font-bold text-lg text-white mb-2 group-hover:text-indigo-400 transition-colors">{card.name}</h3>
              <p className="text-sm text-slate-400 leading-relaxed bg-slate-950/60 p-2 rounded border border-slate-800/40">{card.text}</p>
            </div>
            <div className="mt-4 pt-3 border-t border-slate-800/60 text-right">
              <span className="text-xs font-medium text-slate-500 px-2 py-0.5 rounded bg-slate-800/40 border border-slate-700/30">{card.rarity}</span>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
}
