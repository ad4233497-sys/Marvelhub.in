<!DOCTYPE html>
<html lang="en" class="scroll-smooth">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Marvel Multiverse Archive & Streaming Hub</title>
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Bebas Neue, Montserrat -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Montserrat:wght@300;400;600;700;900&display=swap" rel="stylesheet">
  <!-- Lucide Icons -->
  <script src="https://unpkg.com/lucide@latest"></script>

  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            marvelRed: '#E62429',
            marvelDarkRed: '#9F1216',
            marvelGold: '#F59E0B',
            bgDeep: '#0B0E14',
            bgCard: '#151922',
            bgCardHover: '#1E2330',
            borderDark: '#262D3D',
          },
          fontFamily: {
            bebas: ['"Bebas Neue"', 'sans-serif'],
            montserrat: ['"Montserrat"', 'sans-serif'],
          }
        }
      }
    }
  </script>
  <style>
    body { font-family: 'Montserrat', sans-serif; }
    .title-font { font-family: 'Bebas Neue', sans-serif; letter-spacing: 0.05em; }
    ::-webkit-scrollbar { width: 8px; }
    ::-webkit-scrollbar-track { background: #0B0E14; }
    ::-webkit-scrollbar-thumb { background: #E62429; border-radius: 4px; }
    .badge-comic { background: linear-gradient(135deg, #3B82F6 0%, #1D4ED8 100%); }
    .badge-mcu { background: linear-gradient(135deg, #E62429 0%, #9F1216 100%); }
    @keyframes soundwave {
      0%, 100% { height: 4px; }
      50% { height: 18px; }
    }
    .wave-bar { animation: soundwave 1s ease-in-out infinite; }
  </style>
</head>
<body class="bg-bgDeep text-gray-200 antialiased selection:bg-marvelRed selection:text-white">

  <!-- ================= TOP NAVIGATION ================= -->
  <header class="sticky top-0 z-40 bg-bgDeep/95 backdrop-blur-md border-b border-borderDark px-4 lg:px-8 py-3 transition-all">
    <div class="max-w-7xl mx-auto flex items-center justify-between gap-4">
      <div class="flex items-center gap-3 cursor-pointer" onclick="window.scrollTo({top: 0, behavior: 'smooth'})">
        <div class="bg-marvelRed text-white px-3 py-1 text-2xl font-black title-font tracking-wider rounded shadow-lg shadow-marvelRed/30">
          MARVEL
        </div>
        <span class="text-sm md:text-lg font-bold uppercase tracking-widest text-gray-300 hidden sm:inline">Multiverse & Stream Archive</span>
      </div>

      <nav class="hidden md:flex items-center gap-6 text-sm font-semibold tracking-wide">
        <a href="#characters" class="hover:text-marvelRed transition">Characters</a>
        <a href="#timeline" class="hover:text-marvelRed transition">MCU Watch Guide</a>
        <a href="#comics" class="hover:text-marvelRed transition">Iconic Comics</a>
        <a href="#soundboard" class="hover:text-marvelRed transition">Soundboard</a>
        <a href="#quiz" class="hover:text-marvelRed transition">S.H.I.E.L.D. Quiz</a>
      </nav>

      <div class="flex items-center gap-2">
        <button onclick="openCharModal()" class="flex items-center gap-1.5 text-xs font-bold uppercase px-3 py-2 bg-marvelRed hover:bg-marvelDarkRed text-white rounded shadow transition">
          <i data-lucide="plus-circle" class="w-3.5 h-3.5"></i>
          <span>Add Hero</span>
        </button>
      </div>
    </div>
  </header>

  <!-- ================= HERO SECTION ================= -->
  <section class="relative py-14 px-4 border-b border-borderDark overflow-hidden bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-marvelRed/20 via-bgDeep to-bgDeep">
    <div class="max-w-5xl mx-auto text-center relative z-10">
      <span class="inline-block px-3 py-1 text-xs font-bold tracking-widest text-marvelGold bg-marvelGold/10 border border-marvelGold/30 rounded-full uppercase mb-4">
        Earth-616 & MCU Earth-199999 Stream Hub
      </span>
      <h1 class="text-5xl md:text-7xl font-black title-font tracking-wide uppercase text-white mb-4">
        Marvel Universe Fan Hub
      </h1>
      <p class="text-gray-400 text-sm md:text-base max-w-2xl mx-auto leading-relaxed mb-8">
        Full database of heroes, actors, and comic runs with direct streaming links to watch every MCU title on official platforms like Disney+, Hotstar, and Prime Video.
      </p>

      <!-- Live Search Bar -->
      <div class="relative max-w-xl mx-auto">
        <i data-lucide="search" class="absolute left-4 top-3.5 w-5 h-5 text-gray-400"></i>
        <input 
          type="text" 
          id="searchInput" 
          onkeyup="filterContent()" 
          placeholder="Search hero, villain, actor, movie, or platform..." 
          class="w-full pl-12 pr-4 py-3 bg-bgCard border border-borderDark rounded-lg focus:outline-none focus:border-marvelRed text-white placeholder-gray-500 shadow-xl transition"
        >
      </div>
    </div>
  </section>

  <!-- ================= MAIN CONTENT WRAPPER ================= -->
  <main class="max-w-7xl mx-auto px-4 lg:px-8 py-12 space-y-20">

    <!-- 1. CHARACTERS & ACTORS DATABASE -->
    <section id="characters">
      <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
        <div>
          <h2 class="text-3xl md:text-4xl font-black title-font tracking-wide text-white uppercase flex items-center gap-3">
            <i data-lucide="shield" class="text-marvelRed w-8 h-8"></i>
            Characters & Actor Encyclopedia
          </h2>
          <p class="text-sm text-gray-400">Every major icon with actor details, comic roots, and direct filmography references.</p>
        </div>

        <!-- Filter pills -->
        <div class="flex flex-wrap gap-2 text-xs font-bold uppercase">
          <button onclick="setFilter('all')" class="filter-pill active px-3 py-1.5 rounded bg-marvelRed text-white" data-filter="all">All (<span id="count-all">0</span>)</button>
          <button onclick="setFilter('Avengers')" class="filter-pill px-3 py-1.5 rounded bg-bgCard border border-borderDark hover:border-gray-500" data-filter="Avengers">Avengers</button>
          <button onclick="setFilter('X-Men')" class="filter-pill px-3 py-1.5 rounded bg-bgCard border border-borderDark hover:border-gray-500" data-filter="X-Men">Mutants</button>
          <button onclick="setFilter('Villain')" class="filter-pill px-3 py-1.5 rounded bg-bgCard border border-borderDark hover:border-gray-500" data-filter="Villain">Villains</button>
          <button onclick="setFilter('Custom')" class="filter-pill px-3 py-1.5 rounded bg-bgCard border border-borderDark text-marvelGold hover:border-marvelGold" data-filter="Custom">Community Made</button>
        </div>
      </div>

      <!-- Character Card Grid -->
      <div id="characterGrid" class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6"></div>

      <!-- Data Portability Bar -->
      <div class="mt-8 p-4 bg-bgCard rounded-lg border border-borderDark flex flex-wrap items-center justify-between gap-4 text-xs">
        <div class="text-gray-400">
          <strong class="text-white">Community Edit Mode:</strong> Your additions save to browser cache. Export the JSON file to share or import someone else's additions.
        </div>
        <div class="flex items-center gap-2">
          <button onclick="exportData()" class="px-3 py-1.5 bg-borderDark hover:bg-slate-700 text-white rounded flex items-center gap-1">
            <i data-lucide="download" class="w-3.5 h-3.5"></i> Export
          </button>
          <label class="px-3 py-1.5 bg-borderDark hover:bg-slate-700 text-white rounded flex items-center gap-1 cursor-pointer">
            <i data-lucide="upload" class="w-3.5 h-3.5"></i> Import JSON
            <input type="file" id="importFile" onchange="importData(event)" class="hidden" accept=".json">
          </label>
        </div>
      </div>
    </section>

    <!-- 2. MCU WATCH TIMELINE WITH STREAMING PARTNERS -->
    <section id="timeline" class="border-t border-borderDark pt-16">
      <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4 mb-6">
        <div>
          <h2 class="text-3xl md:text-4xl font-black title-font tracking-wide text-white uppercase flex items-center gap-3">
            <i data-lucide="film" class="text-marvelRed w-8 h-8"></i>
            MCU Timeline & Streaming Partners
          </h2>
          <p class="text-sm text-gray-400">Chronological or Phase-by-phase viewing order with one-click direct links to stream.</p>
        </div>
        <div class="bg-bgCard p-1 rounded-lg border border-borderDark flex text-xs font-bold uppercase">
          <button id="btnOrderRelease" onclick="setTimelineView('release')" class="px-3 py-1.5 rounded bg-marvelRed text-white">Release Phases</button>
          <button id="btnOrderChrono" onclick="setTimelineView('chrono')" class="px-3 py-1.5 rounded text-gray-400 hover:text-white">Story Order</button>
        </div>
      </div>

      <!-- Quick Streaming Hub Launcher -->
      <div class="p-4 mb-8 bg-gradient-to-r from-bgCard via-borderDark/40 to-bgCard rounded-xl border border-borderDark flex flex-wrap items-center justify-between gap-4">
        <div class="flex items-center gap-3">
          <i data-lucide="play-circle" class="w-6 h-6 text-marvelGold"></i>
          <div>
            <span class="text-xs font-bold text-white uppercase block">Official Marvel Streaming Portals</span>
            <span class="text-[11px] text-gray-400">Direct studio destinations:</span>
          </div>
        </div>
        <div class="flex flex-wrap items-center gap-2 text-xs font-bold uppercase">
          <a href="https://www.disneyplus.com" target="_blank" rel="noopener" class="px-3 py-1.5 bg-[#001D47] hover:bg-[#002C6C] text-blue-200 border border-blue-500/30 rounded flex items-center gap-1.5 transition">
            <i data-lucide="external-link" class="w-3.5 h-3.5"></i> Disney+ (Global)
          </a>
          <a href="https://www.hotstar.com/in/studios/marvel/1260021091" target="_blank" rel="noopener" class="px-3 py-1.5 bg-[#0C1B2A] hover:bg-[#132A42] text-yellow-300 border border-yellow-500/30 rounded flex items-center gap-1.5 transition">
            <i data-lucide="tv" class="w-3.5 h-3.5"></i> JioHotstar (India)
          </a>
          <a href="https://www.primevideo.com" target="_blank" rel="noopener" class="px-3 py-1.5 bg-[#002B49] hover:bg-[#003C66] text-sky-300 border border-sky-500/30 rounded flex items-center gap-1.5 transition">
            <i data-lucide="video" class="w-3.5 h-3.5"></i> Prime Video
          </a>
          <a href="https://tv.apple.com" target="_blank" rel="noopener" class="px-3 py-1.5 bg-neutral-800 hover:bg-neutral-700 text-white border border-neutral-600 rounded flex items-center gap-1.5 transition">
            <i data-lucide="monitor" class="w-3.5 h-3.5"></i> Apple TV
          </a>
        </div>
      </div>

      <!-- Timeline Entries Container -->
      <div id="timelineContainer" class="relative border-l-2 border-borderDark ml-4 md:ml-28 space-y-8"></div>
    </section>

    <!-- 3. ICONIC COMIC BOOK SAGA ARCS -->
    <section id="comics" class="border-t border-borderDark pt-16">
      <div class="mb-8">
        <h2 class="text-3xl md:text-4xl font-black title-font tracking-wide text-white uppercase flex items-center gap-3">
          <i data-lucide="book-open" class="text-marvelRed w-8 h-8"></i>
          Legendary Comic Book Arcs
        </h2>
        <p class="text-sm text-gray-400">The comic origins behind Infinity War, Secret Wars, and Civil War.</p>
      </div>
      <div id="comicGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6"></div>
    </section>

    <!-- 4. SOUNDBOARD & S.H.I.E.L.D. TRIVIA QUIZ -->
    <section id="soundboard" class="border-t border-borderDark pt-16 grid grid-cols-1 lg:grid-cols-2 gap-8">
      
      <!-- Catchphrase Soundboard with Guaranteed Audio -->
      <div class="bg-bgCard p-6 rounded-xl border border-borderDark flex flex-col justify-between">
        <div>
          <div class="flex items-center justify-between mb-2">
            <h3 class="text-2xl font-black title-font text-white uppercase flex items-center gap-2">
              <i data-lucide="volume-2" class="text-marvelGold w-6 h-6"></i>
              Hero Voice & SFX Soundboard
            </h3>
            <!-- Audio visualizer bars -->
            <div id="audioVisualizer" class="hidden items-end gap-1 h-5">
              <div class="w-1 bg-marvelRed wave-bar" style="animation-delay: 0.1s"></div>
              <div class="w-1 bg-marvelGold wave-bar" style="animation-delay: 0.3s"></div>
              <div class="w-1 bg-marvelRed wave-bar" style="animation-delay: 0.2s"></div>
              <div class="w-1 bg-white wave-bar" style="animation-delay: 0.4s"></div>
            </div>
          </div>
          <p class="text-xs text-gray-400 mb-6">Equipped with a dual-engine synthesizer (Web Speech + Web Audio Synth) to guarantee playback across all browsers and iframes.</p>
          <div class="grid grid-cols-2 gap-3" id="quoteBoard"></div>
        </div>
        <div id="soundStatus" class="text-xs text-marvelGold/80 mt-4 text-center font-medium bg-bgDeep/60 py-2 rounded border border-borderDark">
          Ready to play. Click any hero quote above!
        </div>
      </div>

      <!-- S.H.I.E.L.D. Clearance Quiz -->
      <div id="quiz" class="bg-bgCard p-6 rounded-xl border border-borderDark">
        <h3 class="text-2xl font-black title-font text-white uppercase flex items-center gap-2 mb-2">
          <i data-lucide="award" class="text-marvelRed w-6 h-6"></i>
          S.H.I.E.L.D. Knowledge Clearance
        </h3>
        <p class="text-xs text-gray-400 mb-6">Test your mastery of Earth-616 and MCU facts.</p>
        
        <div id="quizBody" class="space-y-4">
          <p id="quizQuestion" class="font-bold text-sm text-gray-200"></p>
          <div id="quizOptions" class="space-y-2"></div>
          <div class="flex items-center justify-between pt-4 border-t border-borderDark">
            <span id="quizScore" class="text-xs font-semibold text-marvelGold">Question 1 of 5</span>
            <button id="quizNextBtn" onclick="nextQuestion()" class="hidden px-4 py-1.5 bg-marvelRed hover:bg-marvelDarkRed text-white text-xs font-bold uppercase rounded">Next</button>
          </div>
        </div>
      </div>
    </section>

  </main>

  <!-- ================= CHARACTER MODAL / DOSSIER ================= -->
  <div id="detailModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-bgCard border border-borderDark max-w-2xl w-full rounded-xl overflow-hidden max-h-[90vh] flex flex-col">
      <div class="relative h-48 bg-slate-900 overflow-hidden">
        <img id="modalCover" src="" class="w-full h-full object-cover opacity-60" alt="Banner">
        <button onclick="closeModal('detailModal')" class="absolute top-4 right-4 bg-black/60 hover:bg-marvelRed text-white p-2 rounded-full transition">
          <i data-lucide="x" class="w-4 h-4"></i>
        </button>
        <div class="absolute bottom-4 left-6">
          <span id="modalUniverse" class="text-[10px] font-black uppercase px-2 py-0.5 rounded text-white mb-1 inline-block"></span>
          <h3 id="modalName" class="text-3xl font-black title-font uppercase text-white"></h3>
          <p id="modalActor" class="text-xs text-marvelGold font-semibold"></p>
        </div>
      </div>
      <div class="p-6 overflow-y-auto space-y-4 text-sm">
        <div>
          <h4 class="font-bold text-gray-300 text-xs uppercase tracking-wider mb-1">Background Bio</h4>
          <p id="modalBio" class="text-gray-400 leading-relaxed"></p>
        </div>

        <div>
          <h4 class="font-bold text-gray-300 text-xs uppercase tracking-wider mb-2">Power Ratings</h4>
          <div id="modalPowerGrid" class="grid grid-cols-2 gap-3 text-xs"></div>
        </div>

        <div class="grid grid-cols-2 gap-4 pt-2 border-t border-borderDark text-xs">
          <div>
            <span class="text-gray-500 uppercase block font-semibold">First Comic Issue</span>
            <span id="modalDebut" class="text-white font-medium"></span>
          </div>
          <div>
            <span class="text-gray-500 uppercase block font-semibold">Signature Arsenal</span>
            <span id="modalGear" class="text-white font-medium"></span>
          </div>
        </div>

        <!-- Quick Streaming Action in Dossier -->
        <div class="pt-3 border-t border-borderDark flex items-center justify-between">
          <span class="text-xs text-gray-400 font-semibold">Watch MCU Appearances:</span>
          <a id="modalWatchLink" href="https://www.hotstar.com/in/studios/marvel/1260021091" target="_blank" rel="noopener" class="px-3 py-1.5 bg-marvelRed hover:bg-marvelDarkRed text-white text-xs font-bold uppercase rounded flex items-center gap-1.5 transition">
            <i data-lucide="play" class="w-3.5 h-3.5 fill-current"></i> Stream on Disney+ / Hotstar
          </a>
        </div>
      </div>
    </div>
  </div>

  <!-- ================= ADD / EDIT CHARACTER MODAL ================= -->
  <div id="addCharModal" class="fixed inset-0 z-50 bg-black/80 backdrop-blur-sm hidden flex items-center justify-center p-4">
    <div class="bg-bgCard border border-borderDark max-w-lg w-full rounded-xl p-6 overflow-y-auto max-h-[90vh]">
      <div class="flex items-center justify-between pb-4 border-b border-borderDark mb-4">
        <h3 class="text-xl font-black title-font uppercase text-white flex items-center gap-2">
          <i data-lucide="user-plus" class="text-marvelRed w-5 h-5"></i>
          Add New Hero / Villain
        </h3>
        <button onclick="closeModal('addCharModal')" class="text-gray-400 hover:text-white">
          <i data-lucide="x" class="w-5 h-5"></i>
        </button>
      </div>

      <form id="characterForm" onsubmit="saveCustomCharacter(event)" class="space-y-4 text-xs">
        <div>
          <label class="block font-semibold uppercase text-gray-300 mb-1">Character Alias *</label>
          <input required type="text" id="newAlias" placeholder="e.g. Doctor Doom, Storm, Moon Knight" class="w-full px-3 py-2 bg-bgDeep border border-borderDark rounded text-white">
        </div>
        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block font-semibold uppercase text-gray-300 mb-1">Real Name</label>
            <input type="text" id="newRealName" placeholder="e.g. Victor Von Doom" class="w-full px-3 py-2 bg-bgDeep border border-borderDark rounded text-white">
          </div>
          <div>
            <label class="block font-semibold uppercase text-gray-300 mb-1">MCU Actor</label>
            <input type="text" id="newActor" placeholder="e.g. Robert Downey Jr." class="w-full px-3 py-2 bg-bgDeep border border-borderDark rounded text-white">
          </div>
        </div>
        <div class="grid grid-cols-2 gap-3">
          <div>
            <label class="block font-semibold uppercase text-gray-300 mb-1">Affiliation / Group</label>
            <select id="newAffiliation" class="w-full px-3 py-2 bg-bgDeep border border-borderDark rounded text-white">
              <option value="Avengers">Avengers</option>
              <option value="X-Men">X-Men</option>
              <option value="Villain">Villains</option>
              <option value="Guardians">Guardians</option>
              <option value="Fantastic Four">Fantastic Four</option>
              <option value="Midnight Sons">Midnight Sons</option>
            </select>
          </div>
          <div>
            <label class="block font-semibold uppercase text-gray-300 mb-1">Primary Continuity</label>
            <select id="newUniverse" class="w-full px-3 py-2 bg-bgDeep border border-borderDark rounded text-white">
              <option value="Earth-616">Earth-616 (Comics)</option>
              <option value="MCU">MCU (Earth-199999)</option>
            </select>
          </div>
        </div>
        <div>
          <label class="block font-semibold uppercase text-gray-300 mb-1">Image URL (JPEG/PNG)</label>
          <input type="url" id="newImage" placeholder="https://..." class="w-full px-3 py-2 bg-bgDeep border border-borderDark rounded text-white">
        </div>
        <div>
          <label class="block font-semibold uppercase text-gray-300 mb-1">Short Biography</label>
          <textarea id="newBio" rows="3" placeholder="Origin, powers, and key conflicts..." class="w-full px-3 py-2 bg-bgDeep border border-borderDark rounded text-white"></textarea>
        </div>
        
        <div>
          <label class="block font-semibold uppercase text-gray-300 mb-2">Power Ratings (1 to 7 scale)</label>
          <div class="grid grid-cols-3 gap-2">
            <div>
              <span class="text-[10px] text-gray-400 uppercase">Intelligence</span>
              <input type="number" id="statInt" min="1" max="7" value="4" class="w-full px-2 py-1 bg-bgDeep border border-borderDark rounded text-white">
            </div>
            <div>
              <span class="text-[10px] text-gray-400 uppercase">Strength</span>
              <input type="number" id="statStr" min="1" max="7" value="4" class="w-full px-2 py-1 bg-bgDeep border border-borderDark rounded text-white">
            </div>
            <div>
              <span class="text-[10px] text-gray-400 uppercase">Speed</span>
              <input type="number" id="statSpd" min="1" max="7" value="3" class="w-full px-2 py-1 bg-bgDeep border border-borderDark rounded text-white">
            </div>
            <div>
              <span class="text-[10px] text-gray-400 uppercase">Durability</span>
              <input type="number" id="statDur" min="1" max="7" value="4" class="w-full px-2 py-1 bg-bgDeep border border-borderDark rounded text-white">
            </div>
            <div>
              <span class="text-[10px] text-gray-400 uppercase">Energy</span>
              <input type="number" id="statNrg" min="1" max="7" value="3" class="w-full px-2 py-1 bg-bgDeep border border-borderDark rounded text-white">
            </div>
            <div>
              <span class="text-[10px] text-gray-400 uppercase">Combat</span>
              <input type="number" id="statCbt" min="1" max="7" value="5" class="w-full px-2 py-1 bg-bgDeep border border-borderDark rounded text-white">
            </div>
          </div>
        </div>

        <button type="submit" class="w-full py-2.5 bg-marvelRed hover:bg-marvelDarkRed text-white font-bold uppercase rounded tracking-wider transition">
          Publish Hero to Archive
        </button>
      </form>
    </div>
  </div>

  <!-- ================= JAVASCRIPT APPLICATION LOGIC ================= -->
  <script>
    // --- 1. DEFAULT RICH CHARACTERS DATABASE ---
    const DEFAULT_CHARACTERS = [
      {
        id: 'ironman',
        alias: 'Iron Man',
        realName: 'Tony Stark',
        actor: 'Robert Downey Jr.',
        affiliation: 'Avengers',
        universe: 'MCU / Earth-616',
        debut: 'Tales of Suspense #39 (1963)',
        gear: 'Mark LXXXV Nanotech Armor, Arc Reactor',
        image: 'https://images.unsplash.com/photo-1635863138275-d9b33299680b?auto=format&fit=crop&w=800&q=80',
        bio: 'Billionaire industrialist and founding member of the Avengers who forged his armored suit to escape captivity and defend the universe.',
        stats: { int: 6, str: 6, spd: 5, dur: 6, nrg: 6, cbt: 4 }
      },
      {
        id: 'cap',
        alias: 'Captain America',
        realName: 'Steve Rogers',
        actor: 'Chris Evans',
        affiliation: 'Avengers',
        universe: 'MCU / Earth-616',
        debut: 'Captain America Comics #1 (1941)',
        gear: 'Vibranium Shield, Super-Soldier Serum',
        image: 'https://images.unsplash.com/photo-1608889175123-8ee362201f81?auto=format&fit=crop&w=800&q=80',
        bio: 'Super-soldier from World War II who stood as the moral compass and tactical commander of Earth’s Mightiest Heroes.',
        stats: { int: 3, str: 4, spd: 3, dur: 4, nrg: 1, cbt: 7 }
      },
      {
        id: 'thor',
        alias: 'Thor Odinson',
        realName: 'Thor',
        actor: 'Chris Hemsworth',
        affiliation: 'Avengers',
        universe: 'MCU / Earth-616',
        debut: 'Journey into Mystery #83 (1962)',
        gear: 'Mjolnir, Stormbreaker',
        image: 'https://images.unsplash.com/photo-1579783900882-c0d3dad7b119?auto=format&fit=crop&w=800&q=80',
        bio: 'The Norse God of Thunder and warrior prince of Asgard who controls lightning and commands mystic weapons.',
        stats: { int: 2, str: 7, spd: 6, dur: 6, nrg: 6, cbt: 5 }
      },
      {
        id: 'spiderman',
        alias: 'Spider-Man',
        realName: 'Peter Parker',
        actor: 'Tom Holland / Tobey Maguire',
        affiliation: 'Avengers',
        universe: 'MCU / Earth-616',
        debut: 'Amazing Fantasy #15 (1962)',
        gear: 'Web-Shooters, Spider-Sense, Iron Spider Suit',
        image: 'https://images.unsplash.com/photo-1604200213928-ba3cf4fc8436?auto=format&fit=crop&w=800&q=80',
        bio: 'Bitten by a radioactive spider, Queens teenager Peter Parker champions responsibility across New York and the cosmos.',
        stats: { int: 4, str: 5, spd: 5, dur: 4, nrg: 1, cbt: 5 }
      },
      {
        id: 'wolverine',
        alias: 'Wolverine',
        realName: 'James "Logan" Howlett',
        actor: 'Hugh Jackman',
        affiliation: 'X-Men',
        universe: 'Earth-616 / MCU',
        debut: 'The Incredible Hulk #181 (1974)',
        gear: 'Adamantium Skeleton & Retractable Claws',
        image: 'https://images.unsplash.com/photo-1563089145-599997674d42?auto=format&fit=crop&w=800&q=80',
        bio: 'Mutant with accelerated cellular healing, enhanced senses, and an unbreakable adamantium skeleton.',
        stats: { int: 2, str: 4, spd: 3, dur: 5, nrg: 1, cbt: 7 }
      },
      {
        id: 'thanos',
        alias: 'Thanos',
        realName: 'Thanos of Titan',
        actor: 'Josh Brolin',
        affiliation: 'Villain',
        universe: 'MCU / Earth-616',
        debut: 'The Invincible Iron Man #55 (1973)',
        gear: 'Infinity Gauntlet, Double-Edged Warblade',
        image: 'https://images.unsplash.com/photo-1534447677768-be436bb09401?auto=format&fit=crop&w=800&q=80',
        bio: 'The Mad Titan obsessed with universal balance who wiped out half of all life using the Six Infinity Stones.',
        stats: { int: 6, str: 7, spd: 4, dur: 7, nrg: 6, cbt: 6 }
      },
      {
        id: 'doom',
        alias: 'Doctor Doom',
        realName: 'Victor Von Doom',
        actor: 'Robert Downey Jr. (Doomsday)',
        affiliation: 'Villain',
        universe: 'Earth-616 / MCU',
        debut: 'The Fantastic Four #5 (1962)',
        gear: 'Titanium Armor, Mystic Sorcery, Doombots',
        image: 'https://images.unsplash.com/photo-1579783902614-a3fb3927b675?auto=format&fit=crop&w=800&q=80',
        bio: 'Ruler of Latveria who combines advanced scientific robotics with arcane sorcery to challenge the multiverse.',
        stats: { int: 6, str: 4, spd: 3, dur: 6, nrg: 6, cbt: 5 }
      },
      {
        id: 'scarletwitch',
        alias: 'Scarlet Witch',
        realName: 'Wanda Maximoff',
        actor: 'Elizabeth Olsen',
        affiliation: 'Avengers',
        universe: 'MCU / Earth-616',
        debut: 'The X-Men #4 (1964)',
        gear: 'Chaos Magic, The Darkhold',
        image: 'https://images.unsplash.com/photo-1518709268805-4e9042af9f23?auto=format&fit=crop&w=800&q=80',
        bio: 'Mythical entity capable of spontaneous reality alteration, probability manipulation, and dark magic.',
        stats: { int: 3, str: 2, spd: 3, dur: 3, nrg: 7, cbt: 3 }
      }
    ];

    // --- 2. MCU MOVIES & SERIES WITH LIVE STREAMING LINKS ---
    const MCU_FILMS = [
      {
        title: "Captain America: The First Avenger",
        year: 2011,
        phase: 1,
        chrono: 1,
        director: "Joe Johnston",
        villain: "Red Skull",
        boxOffice: "$370 Million",
        hotstarUrl: "https://www.hotstar.com/in/movies/captain-america-the-first-avenger/1260018448",
        disneyUrl: "https://www.disneyplus.com/movies/captain-america-the-first-avenger/6G59Wj18FzG9",
        justWatchUrl: "https://www.justwatch.com/find?q=Captain%20America%20The%20First%20Avenger"
      },
      {
        title: "Captain Marvel",
        year: 2019,
        phase: 3,
        chrono: 2,
        director: "Anna Boden, Ryan Fleck",
        villain: "Yon-Rogg",
        boxOffice: "$1.13 Billion",
        hotstarUrl: "https://www.hotstar.com/in/movies/captain-marvel/1260014777",
        disneyUrl: "https://www.disneyplus.com/movies/captain-marvel/38MmUv2d9eKq",
        justWatchUrl: "https://www.justwatch.com/find?q=Captain%20Marvel"
      },
      {
        title: "Iron Man",
        year: 2008,
        phase: 1,
        chrono: 3,
        director: "Jon Favreau",
        villain: "Obadiah Stane",
        boxOffice: "$585 Million",
        hotstarUrl: "https://www.hotstar.com/in/movies/iron-man/1260018452",
        disneyUrl: "https://www.disneyplus.com/movies/iron-man/4fF0w6q8H8rD",
        justWatchUrl: "https://www.justwatch.com/find?q=Iron%20Man%202008"
      },
      {
        title: "The Avengers",
        year: 2012,
        phase: 1,
        chrono: 6,
        director: "Joss Whedon",
        villain: "Loki / Chitauri Army",
        boxOffice: "$1.52 Billion",
        hotstarUrl: "https://www.hotstar.com/in/movies/marvels-the-avengers/1260018449",
        disneyUrl: "https://www.disneyplus.com/movies/marvels-the-avengers/2AJ9Lw0e4Fq3",
        justWatchUrl: "https://www.justwatch.com/find?q=The%20Avengers%202012"
      },
      {
        title: "Captain America: The Winter Soldier",
        year: 2014,
        phase: 2,
        chrono: 9,
        director: "Anthony & Joe Russo",
        villain: "Hydra / Winter Soldier",
        boxOffice: "$714 Million",
        hotstarUrl: "https://www.hotstar.com/in/movies/captain-america-the-winter-soldier/1260018451",
        disneyUrl: "https://www.disneyplus.com/movies/captain-america-the-winter-soldier/6h5kU0e8Fq9A",
        justWatchUrl: "https://www.justwatch.com/find?q=Captain%20America%20The%20Winter%20Soldier"
      },
      {
        title: "Avengers: Infinity War",
        year: 2018,
        phase: 3,
        chrono: 19,
        director: "Anthony & Joe Russo",
        villain: "Thanos & The Black Order",
        boxOffice: "$2.05 Billion",
        hotstarUrl: "https://www.hotstar.com/in/movies/avengers-infinity-war/1260018455",
        disneyUrl: "https://www.disneyplus.com/movies/avengers-infinity-war/1271325275",
        justWatchUrl: "https://www.justwatch.com/find?q=Avengers%20Infinity%20War"
      },
      {
        title: "Avengers: Endgame",
        year: 2019,
        phase: 3,
        chrono: 22,
        director: "Anthony & Joe Russo",
        villain: "2014 Thanos",
        boxOffice: "$2.79 Billion",
        hotstarUrl: "https://www.hotstar.com/in/movies/avengers-endgame/1260018456",
        disneyUrl: "https://www.disneyplus.com/movies/avengers-endgame/a8e0f9b3",
        justWatchUrl: "https://www.justwatch.com/find?q=Avengers%20Endgame"
      },
      {
        title: "Deadpool & Wolverine",
        year: 2024,
        phase: 5,
        chrono: 34,
        director: "Shawn Levy",
        villain: "Cassandra Nova",
        boxOffice: "$1.33 Billion",
        hotstarUrl: "https://www.hotstar.com/in/movies/deadpool-and-wolverine/1271325279",
        disneyUrl: "https://www.disneyplus.com/movies/deadpool-and-wolverine/4g8h9u2m",
        justWatchUrl: "https://www.justwatch.com/find?q=Deadpool%20and%20Wolverine"
      }
    ];

    // --- 3. COMIC SAGA ARCS ---
    const COMIC_ARCS = [
      {
        title: "The Infinity Gauntlet (1991)",
        writer: "Jim Starlin",
        pivotalIssue: "Infinity Gauntlet #1-6",
        description: "Thanos collects all six Infinity Gems to extinguish half the universe for Mistress Death. The core inspiration for MCU Phase 3."
      },
      {
        title: "Secret Wars (1984 & 2015)",
        writer: "Jim Shooter (1984) / Jonathan Hickman (2015)",
        pivotalIssue: "Secret Wars #1-9",
        description: "Incursions cause multiverse realities to collide into Battleworld, ruled by God Emperor Doom."
      },
      {
        title: "Civil War (2006)",
        writer: "Mark Millar",
        pivotalIssue: "Civil War #1-7",
        description: "Superheroes divide over government oversight: Tony Stark leads the Pro-Registration side and Steve Rogers leads the resistance."
      },
      {
        title: "Planet Hulk / World War Hulk (2006-2007)",
        writer: "Greg Pak",
        pivotalIssue: "Incredible Hulk #92-105",
        description: "Banished by the Illuminati, Hulk conquers planet Sakaar before returning to Earth to seek vengeance."
      }
    ];

    // --- 4. GUARANTEED DUAL-ENGINE AUDIO SOUNDBOARD ---
    const QUOTES = [
      { speaker: "Iron Man", quote: "I am Iron Man.", sfx: "repulsor" },
      { speaker: "Captain America", quote: "Avengers, assemble!", sfx: "shield" },
      { speaker: "Thor", quote: "Bring me Thanos!", sfx: "thunder" },
      { speaker: "Black Panther", quote: "Wakanda Forever!", sfx: "kinetic" },
      { speaker: "Spider-Man", quote: "With great power comes great responsibility.", sfx: "web" },
      { speaker: "Thanos", quote: "I am inevitable.", sfx: "snap" }
    ];

    // Guaranteed Web Audio API Sound Synthesizer
    let audioCtx = null;

    function getAudioContext() {
      if (!audioCtx) {
        const AudioContext = window.AudioContext || window.webkitAudioContext;
        if (AudioContext) {
          audioCtx = new AudioContext();
        }
      }
      if (audioCtx && audioCtx.state === 'suspended') {
        audioCtx.resume();
      }
      return audioCtx;
    }

    function playCinematicSFX(type) {
      try {
        const ctx = getAudioContext();
        if (!ctx) return;

        const osc = ctx.createOscillator();
        const gain = ctx.createGain();
        osc.connect(gain);
        gain.connect(ctx.destination);

        const now = ctx.currentTime;

        if (type === 'repulsor') {
          // Iron Man Repulsor Charge & Blast
          osc.type = 'sine';
          osc.frequency.setValueAtTime(300, now);
          osc.frequency.exponentialRampToValueAtTime(1400, now + 0.25);
          gain.gain.setValueAtTime(0.3, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.35);
          osc.start(now);
          osc.stop(now + 0.35);
        } else if (type === 'thunder') {
          // Thor Lightning Shockwave
          osc.type = 'sawtooth';
          osc.frequency.setValueAtTime(120, now);
          osc.frequency.exponentialRampToValueAtTime(40, now + 0.4);
          gain.gain.setValueAtTime(0.4, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.45);
          osc.start(now);
          osc.stop(now + 0.45);
        } else if (type === 'shield') {
          // Vibranium Ricochet Ping
          osc.type = 'triangle';
          osc.frequency.setValueAtTime(880, now);
          osc.frequency.exponentialRampToValueAtTime(440, now + 0.3);
          gain.gain.setValueAtTime(0.3, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
          osc.start(now);
          osc.stop(now + 0.3);
        } else {
          // Deep Cosmic Impact
          osc.type = 'square';
          osc.frequency.setValueAtTime(150, now);
          osc.frequency.exponentialRampToValueAtTime(50, now + 0.3);
          gain.gain.setValueAtTime(0.25, now);
          gain.gain.exponentialRampToValueAtTime(0.01, now + 0.3);
          osc.start(now);
          osc.stop(now + 0.3);
        }
      } catch (err) {
        console.warn("Web Audio API not supported in this container:", err);
      }
    }

    function playSoundboardHero(speaker, quote, sfx) {
      // 1. Play immediate synthesizer sound effect (guaranteed audible)
      playCinematicSFX(sfx);

      // Show live sound wave animation
      const vis = document.getElementById('audioVisualizer');
      const status = document.getElementById('soundStatus');
      if (vis) vis.classList.remove('hidden'), vis.classList.add('flex');
      if (status) status.innerHTML = `<span class="text-white font-bold">${speaker}:</span> "${quote}"`;

      // 2. Play Web Speech Voice Synthesizer
      if ('speechSynthesis' in window) {
        window.speechSynthesis.cancel(); // Clears any frozen queue
        const utterance = new SpeechSynthesisUtterance(quote);
        utterance.rate = 0.95;
        utterance.pitch = (speaker === 'Thanos' || speaker === 'Thor') ? 0.75 : 1.0;

        utterance.onend = () => {
          if (vis) vis.classList.add('hidden'), vis.classList.remove('flex');
        };
        utterance.onerror = () => {
          if (vis) vis.classList.add('hidden'), vis.classList.remove('flex');
        };

        window.speechSynthesis.speak(utterance);
      }

      setTimeout(() => {
        if (vis) vis.classList.add('hidden'), vis.classList.remove('flex');
      }, 2000);
    }

    // --- 5. QUIZ DATA ---
    const QUIZ_DATA = [
      {
        q: "What metal is explicitly bonded to Wolverine's skeleton?",
        options: ["Vibranium", "Adamantium", "Uru", "Carbonadium"],
        answer: 1,
        fact: "Adamantium is the virtually indestructible man-made steel alloy."
      },
      {
        q: "Who was the director of S.H.I.E.L.D. that initiated the Avengers Initiative?",
        options: ["Phil Coulson", "Alexander Pierce", "Nick Fury", "Maria Hill"],
        answer: 2,
        fact: "Nick Fury brought the heroes together in 2012."
      },
      {
        q: "Which comic series directly inspired Thor: Ragnarok's gladiator scenes?",
        options: ["Planet Hulk", "Secret Invasion", "Annihilation", "House of M"],
        answer: 0,
        fact: "Planet Hulk featured Hulk fighting in the gladiatorial arenas of Sakaar."
      },
      {
        q: "What is the designation for the prime comic continuity Marvel universe?",
        options: ["Earth-199999", "Earth-838", "Earth-616", "Earth-1610"],
        answer: 2,
        fact: "Earth-616 is the foundational Marvel comic universe created by Alan Moore."
      },
      {
        q: "Which stone was concealed inside the Eye of Agamotto?",
        options: ["Mind Stone", "Time Stone", "Space Stone", "Reality Stone"],
        answer: 1,
        fact: "The Time Stone was guarded by Masters of the Mystic Arts inside the talisman."
      }
    ];

    // --- STATE INITIALIZATION ---
    let characters = JSON.parse(localStorage.getItem('marvel_chars')) || DEFAULT_CHARACTERS;
    let currentFilter = 'all';
    let currentQuizIdx = 0;
    let quizScore = 0;

    // --- APP RENDER FUNCTIONS ---
    function renderCharacters() {
      const grid = document.getElementById('characterGrid');
      grid.innerHTML = '';

      const query = document.getElementById('searchInput').value.toLowerCase();
      const filtered = characters.filter(c => {
        const matchesFilter = currentFilter === 'all' || 
          (currentFilter === 'Custom' && c.isCustom) ||
          c.affiliation === currentFilter;
        const matchesSearch = c.alias.toLowerCase().includes(query) ||
          c.realName.toLowerCase().includes(query) ||
          c.actor.toLowerCase().includes(query) ||
          c.bio.toLowerCase().includes(query);
        return matchesFilter && matchesSearch;
      });

      document.getElementById('count-all').innerText = characters.length;

      filtered.forEach(c => {
        const card = document.createElement('div');
        card.className = "bg-bgCard rounded-xl border border-borderDark hover:border-marvelRed overflow-hidden transition-all duration-300 flex flex-col group shadow-lg";
        card.innerHTML = `
          <div class="relative h-44 overflow-hidden bg-slate-900">
            <img src="${c.image}" alt="${c.alias}" class="w-full h-full object-cover group-hover:scale-105 transition duration-500" onerror="this.src='https://images.unsplash.com/photo-1612036782180-6f0b6cd846fe?auto=format&fit=crop&w=800&q=80'">
            <span class="absolute top-2 right-2 text-[10px] font-black uppercase px-2 py-0.5 rounded text-white ${c.universe.includes('MCU') ? 'badge-mcu' : 'badge-comic'}">
              ${c.universe}
            </span>
          </div>
          <div class="p-4 flex-1 flex flex-col justify-between">
            <div>
              <div class="flex items-center justify-between mb-1">
                <h4 class="font-black title-font text-xl text-white tracking-wide">${c.alias}</h4>
                <span class="text-[10px] text-gray-400 uppercase font-semibold">${c.affiliation}</span>
              </div>
              <p class="text-xs text-marvelGold font-semibold mb-2">${c.actor}</p>
              <p class="text-xs text-gray-400 line-clamp-2 leading-relaxed mb-4">${c.bio}</p>
            </div>
            
            <div class="space-y-2 pt-2 border-t border-borderDark/60">
              <div class="flex justify-between text-[10px] text-gray-400">
                <span>Power Index</span>
                <span class="font-bold text-marvelRed">${Math.round((c.stats.int + c.stats.str + c.stats.spd + c.stats.dur + c.stats.nrg + c.stats.cbt)/6)} / 7</span>
              </div>
              <button onclick="openDetailModal('${c.id}')" class="w-full py-1.5 bg-borderDark hover:bg-marvelRed text-white text-xs font-bold uppercase rounded transition">
                View Dossier & Watch
              </button>
            </div>
          </div>
        `;
        grid.appendChild(card);
      });
      lucide.createIcons();
    }

    function renderTimeline(mode = 'release') {
      const container = document.getElementById('timelineContainer');
      container.innerHTML = '';
      const list = [...MCU_FILMS].sort((a,b) => mode === 'release' ? a.year - b.year : a.chrono - b.chrono);

      list.forEach((m) => {
        const item = document.createElement('div');
        item.className = "relative pl-6 md:pl-8 group";
        item.innerHTML = `
          <div class="absolute -left-[9px] top-1.5 w-4 h-4 rounded-full bg-marvelRed border-4 border-bgDeep group-hover:scale-125 transition"></div>
          <div class="bg-bgCard p-5 rounded-lg border border-borderDark hover:border-gray-500 transition">
            <div class="flex flex-wrap items-center justify-between gap-2 mb-2">
              <h4 class="font-bold text-white text-base">${m.title}</h4>
              <span class="text-xs font-mono font-bold text-marvelGold px-2 py-0.5 bg-marvelGold/10 rounded border border-marvelGold/30">${m.year}</span>
            </div>
            <div class="flex flex-wrap gap-x-4 gap-y-1 text-xs text-gray-400 mb-3">
              <span><strong>Phase:</strong> ${m.phase}</span>
              <span><strong>Timeline Order:</strong> #${m.chrono}</span>
              <span><strong>Director:</strong> ${m.director}</span>
              <span><strong>Antagonist:</strong> ${m.villain}</span>
            </div>

            <div class="pt-3 border-t border-borderDark/80 flex flex-wrap items-center justify-between gap-3">
              <div class="text-[11px] text-gray-500 font-medium">
                Box Office: <span class="text-gray-300 font-semibold">${m.boxOffice}</span>
              </div>
              <div class="flex flex-wrap items-center gap-2 text-xs font-bold uppercase">
                <a href="${m.hotstarUrl}" target="_blank" rel="noopener" class="px-2.5 py-1.5 bg-[#0C1B2A] hover:bg-yellow-600/30 text-yellow-300 border border-yellow-500/40 rounded flex items-center gap-1 transition" title="Stream on Hotstar (India)">
                  <i data-lucide="play" class="w-3 h-3 fill-current"></i> Hotstar
                </a>
                <a href="${m.disneyUrl}" target="_blank" rel="noopener" class="px-2.5 py-1.5 bg-[#001D47] hover:bg-blue-600/30 text-blue-200 border border-blue-500/40 rounded flex items-center gap-1 transition" title="Stream on Disney+">
                  <i data-lucide="external-link" class="w-3 h-3"></i> Disney+
                </a>
                <a href="${m.justWatchUrl}" target="_blank" rel="noopener" class="px-2.5 py-1.5 bg-borderDark hover:bg-slate-700 text-gray-300 rounded flex items-center gap-1 transition" title="Find rental or local options">
                  <i data-lucide="search" class="w-3 h-3"></i> Find Options
                </a>
              </div>
            </div>
          </div>
        `;
        container.appendChild(item);
      });
      lucide.createIcons();
    }

    function renderComics() {
      const grid = document.getElementById('comicGrid');
      grid.innerHTML = '';
      COMIC_ARCS.forEach(arc => {
        const card = document.createElement('div');
        card.className = "bg-bgCard p-5 rounded-xl border border-borderDark hover:border-marvelRed transition flex flex-col justify-between";
        card.innerHTML = `
          <div>
            <span class="text-[10px] font-bold uppercase text-marvelGold tracking-widest block mb-1">Cornerstone Series</span>
            <h4 class="font-black title-font text-xl text-white tracking-wide mb-2">${arc.title}</h4>
            <p class="text-xs text-gray-400 mb-4 leading-relaxed">${arc.description}</p>
          </div>
          <div class="pt-3 border-t border-borderDark text-[11px] text-gray-500 space-y-1">
            <div>Writer/Creative: <span class="text-gray-300">${arc.writer}</span></div>
            <div>Pivotal Run: <span class="text-gray-300 font-mono">${arc.pivotalIssue}</span></div>
          </div>
        `;
        grid.appendChild(card);
      });
    }

    function renderSoundboard() {
      const board = document.getElementById('quoteBoard');
      board.innerHTML = '';
      QUOTES.forEach(q => {
        const btn = document.createElement('button');
        btn.onclick = () => playSoundboardHero(q.speaker, q.quote, q.sfx);
        btn.className = "p-3 bg-bgDeep hover:bg-marvelRed/20 border border-borderDark hover:border-marvelRed rounded text-left transition group active:scale-95";
        btn.innerHTML = `
          <div class="flex items-center justify-between mb-1">
            <span class="text-[10px] uppercase font-bold text-marvelGold group-hover:text-white">${q.speaker}</span>
            <i data-lucide="play" class="w-3 h-3 text-marvelRed group-hover:fill-current"></i>
          </div>
          <span class="text-xs text-gray-200 font-medium block">"${q.quote}"</span>
        `;
        board.appendChild(btn);
      });
      lucide.createIcons();
    }

    // --- FILTER & INTERACTION HANDLERS ---
    function setFilter(category) {
      currentFilter = category;
      document.querySelectorAll('.filter-pill').forEach(btn => {
        btn.classList.toggle('bg-marvelRed', btn.dataset.filter === category);
        btn.classList.toggle('text-white', btn.dataset.filter === category);
      });
      renderCharacters();
    }

    function filterContent() {
      renderCharacters();
    }

    function setTimelineView(mode) {
      document.getElementById('btnOrderRelease').className = mode === 'release' ? 'px-3 py-1.5 rounded bg-marvelRed text-white' : 'px-3 py-1.5 rounded text-gray-400 hover:text-white';
      document.getElementById('btnOrderChrono').className = mode === 'chrono' ? 'px-3 py-1.5 rounded bg-marvelRed text-white' : 'px-3 py-1.5 rounded text-gray-400 hover:text-white';
      renderTimeline(mode);
    }

    // --- DOSSIER MODAL ---
    function openDetailModal(charId) {
      const c = characters.find(item => item.id === charId);
      if (!c) return;

      document.getElementById('modalCover').src = c.image;
      document.getElementById('modalName').innerText = c.alias;
      document.getElementById('modalActor').innerText = `${c.realName} | Portrayed by ${c.actor}`;
      document.getElementById('modalBio').innerText = c.bio;
      document.getElementById('modalDebut').innerText = c.debut || 'Classified';
      document.getElementById('modalGear').innerText = c.gear || 'Standard Combat Arsenal';
      document.getElementById('modalUniverse').innerText = c.universe;

      const grid = document.getElementById('modalPowerGrid');
      grid.innerHTML = '';
      const statMap = [
        { label: 'Intelligence', val: c.stats.int },
        { label: 'Strength', val: c.stats.str },
        { label: 'Speed', val: c.stats.spd },
        { label: 'Durability', val: c.stats.dur },
        { label: 'Energy Projection', val: c.stats.nrg },
        { label: 'Fighting Skill', val: c.stats.cbt }
      ];

      statMap.forEach(s => {
        const row = document.createElement('div');
        row.innerHTML = `
          <div class="flex justify-between mb-1">
            <span class="text-gray-400">${s.label}</span>
            <span class="font-bold text-marvelGold">${s.val}/7</span>
          </div>
          <div class="w-full bg-bgDeep h-1.5 rounded-full overflow-hidden">
            <div class="bg-marvelRed h-full" style="width: ${(s.val/7)*100}%"></div>
          </div>
        `;
        grid.appendChild(row);
      });

      document.getElementById('detailModal').classList.remove('hidden');
    }

    function openCharModal() { document.getElementById('addCharModal').classList.remove('hidden'); }
    function closeModal(id) { document.getElementById(id).classList.add('hidden'); }

    // --- SAVE CUSTOM CHARACTER ---
    function saveCustomCharacter(e) {
      e.preventDefault();
      const alias = document.getElementById('newAlias').value.trim();
      const realName = document.getElementById('newRealName').value.trim() || alias;
      const actor = document.getElementById('newActor').value.trim() || 'Comic Incarnation';
      const affiliation = document.getElementById('newAffiliation').value;
      const universe = document.getElementById('newUniverse').value;
      const image = document.getElementById('newImage').value.trim() || 'https://images.unsplash.com/photo-1612036782180-6f0b6cd846fe?auto=format&fit=crop&w=800&q=80';
      const bio = document.getElementById('newBio').value.trim() || 'Classified S.H.I.E.L.D. archive profile.';

      const newChar = {
        id: 'custom_' + Date.now(),
        alias,
        realName,
        actor,
        affiliation,
        universe,
        image,
        bio,
        debut: 'Community Archive Entry',
        gear: 'Autonomous Arsenal',
        isCustom: true,
        stats: {
          int: parseInt(document.getElementById('statInt').value) || 4,
          str: parseInt(document.getElementById('statStr').value) || 4,
          spd: parseInt(document.getElementById('statSpd').value) || 3,
          dur: parseInt(document.getElementById('statDur').value) || 4,
          nrg: parseInt(document.getElementById('statNrg').value) || 3,
          cbt: parseInt(document.getElementById('statCbt').value) || 4,
        }
      };

      characters.unshift(newChar);
      localStorage.setItem('marvel_chars', JSON.stringify(characters));
      closeModal('addCharModal');
      document.getElementById('characterForm').reset();
      renderCharacters();
    }

    // --- EXPORT & IMPORT ---
    function exportData() {
      const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(characters, null, 2));
      const downloadAnchor = document.createElement('a');
      downloadAnchor.setAttribute("href", dataStr);
      downloadAnchor.setAttribute("download", "marvel_multiverse_database.json");
      document.body.appendChild(downloadAnchor);
      downloadAnchor.click();
      downloadAnchor.remove();
    }

    function importData(event) {
      const file = event.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(e) {
        try {
          const imported = JSON.parse(e.target.result);
          if (Array.isArray(imported)) {
            characters = imported;
            localStorage.setItem('marvel_chars', JSON.stringify(characters));
            renderCharacters();
            alert("Marvel Archive successfully updated from file!");
          }
        } catch (err) {
          alert("Invalid JSON format.");
        }
      };
      reader.readAsText(file);
    }

    // --- S.H.I.E.L.D. TRIVIA GAME ---
    function renderQuiz() {
      if (currentQuizIdx >= QUIZ_DATA.length) {
        document.getElementById('quizBody').innerHTML = `
          <div class="text-center py-6">
            <h4 class="text-2xl font-black title-font text-white uppercase mb-2">Evaluation Complete</h4>
            <p class="text-sm text-gray-400 mb-4">You scored <strong class="text-marvelGold">${quizScore} / ${QUIZ_DATA.length}</strong> on the clearance exam.</p>
            <button onclick="resetQuiz()" class="px-4 py-2 bg-marvelRed text-white text-xs font-bold uppercase rounded">Retake Examination</button>
          </div>
        `;
        return;
      }

      const q = QUIZ_DATA[currentQuizIdx];
      document.getElementById('quizQuestion').innerText = `${currentQuizIdx + 1}. ${q.q}`;
      document.getElementById('quizScore').innerText = `Question ${currentQuizIdx + 1} of ${QUIZ_DATA.length}`;
      document.getElementById('quizNextBtn').classList.add('hidden');

      const optionsContainer = document.getElementById('quizOptions');
      optionsContainer.innerHTML = '';

      q.options.forEach((opt, idx) => {
        const btn = document.createElement('button');
        btn.className = "w-full text-left px-3 py-2 bg-bgDeep hover:bg-slate-800 border border-borderDark rounded text-xs text-gray-300 transition flex items-center justify-between";
        btn.innerText = opt;
        btn.onclick = () => selectQuizAnswer(idx, q.answer, q.fact);
        optionsContainer.appendChild(btn);
      });
    }

    function selectQuizAnswer(selected, correct, fact) {
      const buttons = document.getElementById('quizOptions').children;
      for (let i = 0; i < buttons.length; i++) {
        buttons[i].disabled = true;
        if (i === correct) {
          buttons[i].classList.add('bg-green-900/40', 'border-green-500', 'text-green-300');
        } else if (i === selected) {
          buttons[i].classList.add('bg-red-900/40', 'border-red-500', 'text-red-300');
        }
      }
      if (selected === correct) quizScore++;
      document.getElementById('quizNextBtn').classList.remove('hidden');
    }

    function nextQuestion() {
      currentQuizIdx++;
      renderQuiz();
    }

    function resetQuiz() {
      currentQuizIdx = 0;
      quizScore = 0;
      location.reload();
    }

    // --- INITIAL BOOTSTRAP ---
    window.addEventListener('DOMContentLoaded', () => {
      renderCharacters();
      renderTimeline();
      renderComics();
      renderSoundboard();
      renderQuiz();
    });
  </script>
</body>
</html>

