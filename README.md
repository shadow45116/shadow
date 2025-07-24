import React, { useState } from "react";

// Placeholder URLs for embeds and links
const PODCAST_EMBED = "https://open.spotify.com/embed/show/placeholder";
const DONATION_LINK = "https://your-wise-link.com";
const NEWSLETTER_FORM_EMBED = "<!-- Mailchimp/ConvertKit Embed Here -->";
const COMMUNITY_EMBED = "<!-- CommentBox/Disqus Embed Here -->";

const cases = [
  {
    id: 1,
    title: "Case: The Vanishing of Jane Doe",
    summary: "A mysterious disappearance in 1992, never solved.",
    link: "#",
  },
  {
    id: 2,
    title: "Case: The Riverbank Mystery",
    summary: "A cold case reopened after new evidence surfaces.",
    link: "#",
  },
  // Add more cases here
];

const files = [
  {
    name: "Case 001 - Jane Doe.pdf",
    url: "/files/Case001-JaneDoe.pdf",
  },
  {
    name: "Podcast Script - Episode 1.docx",
    url: "/files/Episode1Script.docx",
  },
  // Add more files here
];

export default function Home() {
  const [search, setSearch] = useState("");

  const filteredCases = cases.filter(
    (c) =>
      c.title.toLowerCase().includes(search.toLowerCase()) ||
      c.summary.toLowerCase().includes(search.toLowerCase())
  );

  return (
    <div className="bg-neutral-900 min-h-screen text-neutral-100 font-sans">
      {/* Hero Section */}
      <section className="relative flex flex-col items-center justify-center h-[60vh] px-4 text-center">
        <div className="absolute inset-0 bg-gradient-to-b from-black/70 to-transparent z-0" />
        <h1 className="relative z-10 text-5xl md:text-7xl font-bold drop-shadow-lg">
          Shadows of the Missing
        </h1>
        <p className="relative z-10 mt-6 text-lg md:text-2xl max-w-2xl mx-auto font-light text-neutral-300">
          Uncovering the untold stories behind true crime disappearances.
        </p>
      </section>

      {/* Support & Donation Section */}
      <section className="px-4 py-8 bg-neutral-800 shadow-inner rounded-xl max-w-2xl mx-auto mb-8">
        <h2 className="text-2xl font-semibold mb-2">Support Our Mission</h2>
        <p className="mb-4 text-neutral-300">
          Your support helps us tell more stories, reach more families, and bring attention to the missing. Every contribution, no matter the size, makes a difference.
        </p>
        <a
          href={DONATION_LINK}
          target="_blank"
          rel="noopener noreferrer"
          className="inline-block px-6 py-3 rounded-lg bg-indigo-600 hover:bg-indigo-700 transition shadow-md text-white font-bold"
        >
          Donate via Wise
        </a>
      </section>

      {/* Podcast Section */}
      <section className="px-4 py-8 max-w-4xl mx-auto mb-8">
        <h2 className="text-2xl font-semibold mb-4">Podcast Episodes</h2>
        <div className="flex flex-wrap gap-4">
          {/* Example embedded player */}
          <iframe
            src={PODCAST_EMBED}
            width="100%"
            height="152"
            frameBorder="0"
            allow="autoplay; clipboard-write; encrypted-media; picture-in-picture"
            className="rounded-lg shadow"
            title="Spotify Podcast Player"
          ></iframe>
          {/* Add more podcast embeds as needed */}
        </div>
      </section>

      {/* Cases Section */}
      <section className="px-4 py-8 max-w-4xl mx-auto mb-8">
        <h2 className="text-2xl font-semibold mb-4">Explore Cases</h2>
        <input
          className="w-full p-2 mb-4 rounded bg-neutral-700 text-neutral-100 placeholder-neutral-400 border border-neutral-800 focus:outline-none focus:ring-2 focus:ring-indigo-600 transition"
          placeholder="Search cases…"
          value={search}
          onChange={(e) => setSearch(e.target.value)}
        />
        <div className="space-y-4">
          {filteredCases.length > 0 ? (
            filteredCases.map((c) => (
              <a
                key={c.id}
                href={c.link}
                className="block p-4 rounded-xl bg-neutral-800 hover:bg-neutral-700 transition shadow"
              >
                <h3 className="font-bold">{c.title}</h3>
                <p className="text-neutral-300">{c.summary}</p>
              </a>
            ))
          ) : (
            <p className="text-neutral-400">No cases found.</p>
          )}
        </div>
      </section>

      {/* File Upload & Download Section */}
      <section className="px-4 py-8 max-w-4xl mx-auto mb-8">
        <h2 className="text-2xl font-semibold mb-4">Case Files & Resources</h2>
        <div className="flex flex-col gap-2">
          {files.map((file) => (
            <a
              href={file.url}
              key={file.name}
              download
              className="p-3 rounded-lg bg-neutral-800 hover:bg-neutral-700 transition shadow flex items-center gap-2"
            >
              <span role="img" aria-label="file" className="text-indigo-400">
                📄
              </span>
              {file.name}
            </a>
          ))}
        </div>
        {/* File upload placeholder for admin dashboard */}
      </section>

      {/* Community Section */}
      <section className="px-4 py-8 max-w-4xl mx-auto mb-8">
        <h2 className="text-2xl font-semibold mb-4">Community Board</h2>
        <div className="bg-neutral-800 rounded-lg shadow p-4">
          <div dangerouslySetInnerHTML={{ __html: COMMUNITY_EMBED }} />
          <p className="text-neutral-400 text-sm mt-2">
            Join the discussion, share tips, or help bring someone home.
          </p>
        </div>
      </section>

      {/* Newsletter Sign-up */}
      <section className="px-4 py-8 max-w-2xl mx-auto mb-8">
        <h2 className="text-2xl font-semibold mb-4">Stay Updated</h2>
        <div
          className="bg-neutral-800 rounded-lg shadow p-4"
          dangerouslySetInnerHTML={{ __html: NEWSLETTER_FORM_EMBED }}
        />
        <p className="text-neutral-400 text-xs mt-2">
          Never miss an update—subscribe for new cases, episodes, and community news.
        </p>
      </section>

      {/* Footer */}
      <footer className="bg-neutral-950 mt-12 py-6 px-4">
        <div className="flex flex-col md:flex-row items-center justify-between max-w-5xl mx-auto gap-6">
          <nav className="flex gap-6 text-neutral-300 text-sm">
            <a href="#" className="hover:text-indigo-400 transition">Home</a>
            <a href="#podcast" className="hover:text-indigo-400 transition">Podcast</a>
            <a href="#cases" className="hover:text-indigo-400 transition">Cases</a>
            <a href="#community" className="hover:text-indigo-400 transition">Community</a>
            <a href="#newsletter" className="hover:text-indigo-400 transition">Newsletter</a>
          </nav>
          <div className="flex gap-4 text-2xl">
            <a href="https://twitter.com/" target="_blank" rel="noopener noreferrer" aria-label="X / Twitter" className="hover:text-indigo-400 transition">
              <i className="fab fa-x-twitter"></i>
            </a>
            <a href="https://instagram.com/" target="_blank" rel="noopener noreferrer" aria-label="Instagram" className="hover:text-indigo-400 transition">
              <i className="fab fa-instagram"></i>
            </a>
            <a href="mailto:contact@shadowsofthemissing.com" aria-label="Email" className="hover:text-indigo-400 transition">
              <i className="far fa-envelope"></i>
            </a>
          </div>
        </div>
        <div className="text-center text-neutral-500 text-xs mt-4">
          &copy; {new Date().getFullYear()} Shadows of the Missing. All rights reserved.
        </div>
      </footer>
    </div>
  );
}import React, { useState } from "react";

const PASSWORD = process.env.NEXT_PUBLIC_ADMIN_PASS || "changeme";

export default function Dashboard() {
  const [input, setInput] = useState("");
  const [authed, setAuthed] = useState(false);

  function handleLogin(e: React.FormEvent) {
    e.preventDefault();
    if (input === PASSWORD) setAuthed(true);
    else alert("Incorrect password.");
  }

  // Placeholder content management displays
  return (
    <div className="bg-neutral-900 min-h-screen text-neutral-100 font-sans flex flex-col items-center py-16 px-4">
      {!authed ? (
        <form onSubmit={handleLogin} className="bg-neutral-800 p-8 rounded-lg shadow-lg flex flex-col items-center">
          <h1 className="text-3xl font-bold mb-6">Admin Dashboard Login</h1>
          <input
            type="password"
            className="rounded p-2 mb-4 bg-neutral-700 text-neutral-100 border border-neutral-600 focus:outline-none focus:ring-2 focus:ring-indigo-600"
            value={input}
            onChange={(e) => setInput(e.target.value)}
            placeholder="Password"
          />
          <button
            className="bg-indigo-600 hover:bg-indigo-700 px-6 py-2 rounded font-semibold shadow text-white transition"
            type="submit"
          >
            Enter
          </button>
        </form>
      ) : (
        <main className="max-w-3xl w-full">
          <h1 className="text-4xl font-bold mb-8 text-center">Shadows of the Missing - Dashboard</h1>
          <div className="bg-neutral-800 p-6 rounded-lg mb-6 shadow">
            <h2 className="text-xl font-semibold mb-4">Case Files Manager</h2>
            {/* Placeholder: Replace with real case management */}
            <ul className="mb-2">
              <li>Case 001 - Jane Doe <button className="ml-2 text-xs text-indigo-400 underline">Edit</button></li>
              <li>Case 002 - Riverbank Mystery <button className="ml-2 text-xs text-indigo-400 underline">Edit</button></li>
            </ul>
            <button className="px-4 py-2 bg-indigo-600 rounded text-white text-sm">Add New Case</button>
          </div>
          <div className="bg-neutral-800 p-6 rounded-lg mb-6 shadow">
            <h2 className="text-xl font-semibold mb-4">Podcast Episodes</h2>
            <ul className="mb-2">
              <li>Episode 1: Disappearance <button className="ml-2 text-xs text-indigo-400 underline">Edit</button></li>
            </ul>
            <button className="px-4 py-2 bg-indigo-600 rounded text-white text-sm">Add New Episode</button>
          </div>
          <div className="bg-neutral-800 p-6 rounded-lg mb-6 shadow">
            <h2 className="text-xl font-semibold mb-4">File Uploads</h2>
            {/* File upload input (placeholder) */}
            <input
              type="file"
              className="block w-full mb-4 text-neutral-200 bg-neutral-700 rounded"
              multiple
              // Implement upload handler
            />
            <ul>
              <li>Case 001 - Jane Doe.pdf <button className="ml-2 text-xs text-red-400 underline">Delete</button></li>
            </ul>
          </div>
          <div className="bg-neutral-800 p-6 rounded-lg mb-6 shadow">
            <h2 className="text-xl font-semibold mb-4">Messages & Community</h2>
            <p>Recent messages and comments (integration with CommentBox/Disqus needed)</p>
          </div>
          <div className="bg-neutral-800 p-6 rounded-lg shadow">
            <h2 className="text-xl font-semibold mb-4">Newsletter Sign-ups</h2>
            <p>Newsletter emails (integration needed)</p>
          </div>
        </main>
      )}
    </div>
  );
}@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;600;700&display=swap');
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css');

html {
  scroll-behavior: smooth;
}

body {
  font-family: 'Montserrat', sans-serif;
  background: #161616;
  color: #e7e7e7;
}

::-webkit-scrollbar {
  width: 8px;
  background: #232323;
}
::-webkit-scrollbar-thumb {
  background: #363636;
  border-radius: 4px;
}/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  env: {
    NEXT_PUBLIC_ADMIN_PASS: process.env.NEXT_PUBLIC_ADMIN_PASS || "changeme",
  },
  // Add more config as needed (file uploads, etc.)
};

module.exports = nextConfig;{
  "name": "shadows-of-the-missing",
  "version": "1.0.0",
  "private": true,
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    "next": "^13.4.0",
    "react": "^18.0.0",
    "react-dom": "^18.0.0"
  },
  "devDependencies": {
    "autoprefixer": "^10.4.0",
    "postcss": "^8.4.0",
    "tailwindcss": "^3.3.0",
    "eslint": "8.56.0"
  }
}/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./pages//*.{ts,tsx,js,jsx}",
    "./components//*.{ts,tsx,js,jsx}"
  ],
  darkMode: "class",
  theme: {
    extend: {
      colors: {
        neutral: {
          900: "#161616",
          950: "#101012",
        }
      },
      fontFamily: {
        sans: ["Montserrat", "sans-serif"]
      }
    }
  },
  plugins: []
};

