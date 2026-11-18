
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Neon Sticky Pad Pro 2500+</title>

<style>
:root {
  --accent: #ff4fd8;
  --ink: #a00085;
  --panel: rgba(20, 15, 45, .88);
}

* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  font-family: "Trebuchet MS", sans-serif;
  color: white;
  background:
    radial-gradient(circle at 15% 20%, #ff6ec7 0, transparent 32%),
    radial-gradient(circle at 85% 15%, #7367ff 0, transparent 32%),
    radial-gradient(circle at 50% 90%, #00d9ff 0, transparent 35%),
    linear-gradient(135deg,#130c35,#25104c,#071c43);
  background-attachment: fixed;
  overflow-x: hidden;
}

/* Anime-inspired background */

body::before {
  content: "✦  ✧  ❀  ✦  ✧  ★  ❀  ✦";
  position: fixed;
  inset: 0;
  z-index: -1;
  font-size: 45px;
  letter-spacing: 35px;
  line-height: 110px;
  color: rgba(255,255,255,.12);
  pointer-events: none;
  animation: float 15s linear infinite;
  overflow: hidden;
}

@keyframes float {
  from { transform: translateY(0); }
  to { transform: translateY(-150px); }
}

header {
  text-align: center;
  padding: 25px 12px;
}

.logo {
  font-size: clamp(27px,5vw,43px);
  font-weight: 900;
  letter-spacing: 2px;
  background: linear-gradient(90deg,#ff72d2,#72faff,#fff08a);
  background-clip: text;
  color: transparent;
  filter: drop-shadow(0 0 15px #ff44cf);
}

header p {
  color: #e5dcff;
  font-size: 13px;
}

.container {
  max-width: 1250px;
  margin: auto;
  padding: 12px;
}

.panel {
  background: var(--panel);
  border: 1px solid rgba(255,255,255,.19);
  border-radius: 18px;
  padding: 17px;
  margin-bottom: 18px;
  box-shadow: 0 0 25px rgba(151,76,255,.2);
  backdrop-filter: blur(15px);
}

.toolbar {
  display: flex;
  flex-wrap: wrap;
  gap: 9px;
  align-items: center;
  justify-content: space-between;
}

button, select, input {
  font: inherit;
}

button {
  border: none;
  cursor: pointer;
  border-radius: 10px;
  padding: 11px 15px;
  color: white;
  background: linear-gradient(135deg,#933cff,#ed43cb);
  box-shadow: 0 0 10px rgba(205,70,255,.3);
  transition: .2s;
}

button:hover {
  transform: translateY(-2px);
  filter: brightness(1.2);
}

button.secondary {
  background: #27214c;
  border: 1px solid #7768ad;
}

button.danger {
  background: #c72d62;
}

input, select {
  background: #17132e;
  color: white;
  border: 1px solid #66568f;
  border-radius: 9px;
  padding: 11px;
  outline: none;
  max-width: 100%;
}

input:focus, select:focus {
  border-color: #ff60db;
  box-shadow: 0 0 8px #ff60db;
}

.stats {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin: 15px 0;
}

.stat {
  flex: 1;
  min-width: 110px;
  padding: 13px;
  border-radius: 12px;
  background: rgba(255,255,255,.09);
  text-align: center;
}

.stat strong {
  display: block;
  font-size: 23px;
  color: #ff8cdd;
}

.editor {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

.editor input, .editor select {
  width: 100%;
}

.editor textarea {
  grid-column: 1 / -1;
  width: 100%;
  min-height: 145px;
  padding: 17px;
  border-radius: 12px;
  resize: vertical;
  border: 2px solid #ff76dc;
  background: rgba(255,255,255,.96);
  color: #5a1683;
  font-size: 17px;
  line-height: 1.7;
  font-family: "Comic Sans MS", cursive;
  outline: none;
}

.editor textarea::placeholder {
  color: #9871a5;
}

.editor textarea:focus {
  box-shadow: 0 0 20px #ff5ddd;
}

.editor-actions {
  grid-column: 1/-1;
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.palette {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin: 12px 0;
}

.color {
  width: 28px;
  height: 28px;
  border: 2px solid white;
  border-radius: 50%;
  cursor: pointer;
  transition: .2s;
}

.color:hover, .color.selected {
  transform: scale(1.22);
  outline: 2px solid #fff;
  outline-offset: 2px;
}

.notes-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill,minmax(230px,1fr));
  gap: 17px;
  margin-top: 18px;
}

.note {
  position: relative;
  min-height: 205px;
  padding: 16px;
  border-radius: 5px 5px 18px 5px;
  background: var(--note-bg);
  color: var(--note-ink);
  box-shadow: 5px 8px 20px rgba(0,0,0,.3);
  transform: rotate(var(--rotation));
  transition: .2s;
  overflow-wrap: anywhere;
}

.note:hover {
  transform: rotate(0deg) translateY(-4px);
  box-shadow: 0 0 20px var(--note-bg);
}

.note h3 {
  margin: 5px 0 10px;
  font-family: "Comic Sans MS", cursive;
  font-size: 19px;
}

.note p {
  font-family: "Comic Sans MS", cursive;
  font-size: 15px;
  line-height: 1.65;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}

.note small {
  opacity: .7;
}

.note-tools {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
  margin-top: 14px;
}

.note-tools button {
  padding: 7px 10px;
  font-size: 12px;
  background: rgba(0,0,0,.65);
  box-shadow: none;
}

.pin {
  position: absolute;
  top: 9px;
  right: 10px;
  font-size: 19px;
  cursor: pointer;
}

.library-title {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: space-between;
  gap: 10px;
}

.section-title {
  color: #ff8ce4;
  font-size: 21px;
}

.footer {
  text-align: center;
  padding: 25px;
  color: #c9b9f9;
  font-size: 12px;
}

.hidden {
  display: none;
}

@media(max-width:600px) {
  .editor {
    grid-template-columns: 1fr;
  }
  .editor textarea, .editor-actions {
    grid-column: 1;
  }
  .toolbar {
    justify-content: flex-start;
  }
  .notes-grid {
    grid-template-columns: 1fr 1fr;
    gap: 10px;
  }
  .note {
    padding: 12px;
    min-height: 180px;
  }
}

@media(max-width:370px) {
  .notes-grid {
    grid-template-columns: 1fr;
  }
}
</style>
</head>

<body>

<header>
  <div class="logo">✦ NEON STICKY PAD ✦</div>
  <p>2500+ Neon Colors • Anime Dreams • Your Personal Note Universe</p>
  <p>Created by Akash Dey | PRO EDITION</p>
</header>

<main class="container">

  <div class="panel toolbar">
    <button onclick="newNote()">＋ New Note</button>
    <button class="secondary" onclick="showLibrary()">📚 Saved Library</button>
    <button class="secondary" onclick="exportNotes()">⬇ Export</button>
    <button class="secondary" onclick="document.getElementById('importFile').click()">⬆ Import</button>
    <button class="secondary" onclick="clearSearch()">↻ Refresh</button>
    <input type="file" id="importFile" accept=".json" hidden onchange="importNotes(event)">
  </div>

  <div class="stats">
    <div class="stat"><strong id="totalNotes">0</strong>All Notes</div>
    <div class="stat"><strong id="savedNotes">0</strong>Saved Notes</div>
    <div class="stat"><strong id="pinnedNotes">0</strong>Pinned Notes</div>
    <div class="stat"><strong>2500+</strong>Neon Colors</div>
  </div>

  <section class="panel" id="editorPanel">
    <h2 class="section-title">✍ Create Your Sticky Note</h2>

    <div class="editor">
      <input id="noteTitle" placeholder="Enter note title...">

      <select id="pageTheme" onchange="updateInk()">
        <option value="#fff0a8">Sunshine Yellow Page</option>
        <option value="#ffc5e8">Anime Pink Page</option>
        <option value="#b9f8ff">Ocean Blue Page</option>
        <option value="#c8ffbc">Mint Green Page</option>
        <option value="#d9c4ff">Dream Purple Page</option>
        <option value="#ffbda7">Peach Page</option>
        <option value="#252044">Midnight Page</option>
        <option value="#ffffff">Classic White Page</option>
        <option value="#202d43">Dark Blue Page</option>
      </select>

      <textarea id="noteContent"
        placeholder="Write your thoughts here... ✨"></textarea>

      <select id="fontStyle" onchange="applyFont()">
        <option value="Comic Sans MS">Anime Handwriting</option>
        <option value="cursive">Classic Handwriting</option>
        <option value="Georgia">Elegant Serif</option>
        <option value="Trebuchet MS">Modern Writing</option>
        <option value="monospace">Typewriter</option>
      </select>

      <select id="inkMode" onchange="updateInk()">
        <option value="auto">Automatic Page Ink</option>
        <option value="black">Black Ink</option>
        <option value="white">White Ink</option>
        <option value="custom">Custom Ink</option>
      </select>

      <div>
        <label>Custom ink:</label>
        <input type="color" id="customInk" value="#7b168c"
          oninput="updateInk()">
      </div>

      <div>
        <label>Note background:</label>
        <input type="color" id="customBg" value="#fff0a8">
      </div>

      <div class="editor-actions">
        <button onclick="saveNote()">💾 Save to Library</button>
        <button class="secondary" onclick="newNote()">Clear Editor</button>
      </div>
    </div>

    <h3 class="section-title">🎨 2500+ Neon Color Universe</h3>
    <p>Choose a handwriting color or a beautiful neon shade.</p>

    <input type="text" id="colorSearch"
      placeholder="Search color e.g. pink, blue, purple..."
      oninput="filterColors()">

    <div class="palette" id="palette"></div>
    <button class="secondary" onclick="generateColors()">✨ Generate More Colors</button>
  </section>

  <section class="panel">
    <div class="library-title">
      <h2 class="section-title">📚 My Sticky Note Library</h2>
      <input id="searchNotes" placeholder="Search notes..."
        oninput="renderNotes()">
    </div>

    <div class="toolbar">
      <select id="sortNotes" onchange="renderNotes()">
        <option value="newest">Newest First</option>
        <option value="oldest">Oldest First</option>
        <option value="pinned">Pinned First</option>
        <option value="az">Title A-Z</option>
      </select>

      <select id="filterNotes" onchange="renderNotes()">
        <option value="all">All Notes</option>
        <option value="pinned">Pinned Only</option>
      </select>
    </div>

    <div class="notes-grid" id="notesGrid"></div>
    <p id="emptyMessage" style="text-align:center;color:#c9b9f9">
      ✨ Your library is empty. Create your first sticky note!
    </p>
  </section>

</main>

<footer class="footer">
  NEON STICKY PAD PRO 2500+ <br>
  Developed with creativity by Akash Dey ✦
  <br> Your thoughts, your colors, your universe.
</footer>

<script>
const STORAGE_KEY = "akash_neon_sticky_pad_v1";

let notes = [];
let colors = [];
let selectedInk = "#a00085";
let editingId = null;

try {
  notes = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
  if (!Array.isArray(notes)) notes = [];
} catch(e) {
  notes = [];
}

// Generate more than 2500 beautiful neon colors

function generateColors() {
  colors = [];

  const colorNames = [
    "Pink","Red","Orange","Yellow","Green",
    "Mint","Cyan","Blue","Purple","Violet",
    "Magenta","Rose","Coral","Gold","Turquoise",
    "Lavender","Lime","Aqua","Indigo","Peach"
  ];

  for(let i=0; i<2600; i++) {
    const hue = (i * 137.508) % 360;
    const saturation = 65 + (i % 35);
    const lightness = 40 + (i % 25);

    const color = `hsl(${hue.toFixed(1)},${saturation}%,${lightness}%)`;

    colors.push({
      value: color,
      name: colorNames[Math.floor(hue/18)%colorNames.length]
    });
  }

  displayColors();
}

function displayColors(list=colors) {
  const palette = document.getElementById("palette");
  palette.innerHTML = "";

  list.slice(0,2600).forEach(c => {
    const div = document.createElement("div");
    div.className = "color";
    div.style.background = c.value;
    div.title = c.name + " - " + c.value;

    div.onclick = () => {
      selectedInk = c.value;
      document.getElementById("inkMode").value = "custom";
      document.getElementById("customInk").value =
        toHex(c.value) || "#ff00cc";
      updateInk();
      document.querySelectorAll(".color").forEach(x =>
        x.classList.remove("selected")
      );
      div.classList.add("selected");
    };

    palette.appendChild(div);
  });
}

function filterColors() {
  const query = document.getElementById("colorSearch")
    .value.toLowerCase();

  const filtered = colors.filter(c =>
    c.name.toLowerCase().includes(query) ||
    c.value.toLowerCase().includes(query)
  );

  displayColors(filtered);
}

function toHex(color) {
  if(color.startsWith("#")) return color;

  const canvas = document.createElement("canvas");
  const ctx = canvas.getContext("2d");
  ctx.fillStyle = color;
  return ctx.fillStyle;
}

// Automatic handwriting color according to page

function updateInk() {
  const mode = document.getElementById("inkMode").value;
  const bg = document.getElementById("pageTheme").value;

  let ink;

  if(mode === "black") {
    ink = "#111111";
  } else if(mode === "white") {
    ink = "#ffffff";
  } else if(mode === "custom") {
    ink = document.getElementById("customInk").value;
  } else {
    ink = contrastInk(bg);
  }

  selectedInk = ink;

  const textarea = document.getElementById("noteContent");
  textarea.style.color = ink;
  textarea.style.background = bg;
}

function contrastInk(hex) {
  const c = hex.replace("#","");
  const r = parseInt(c.substring(0,2),16);
  const g = parseInt(c.substring(2,4),16);
  const b = parseInt(c.substring(4,6),16);

  const brightness = (r*299 + g*587 + b*114)/1000;

  return brightness > 145 ? "#38204b" : "#ffffff";
}

function applyFont() {
  document.getElementById("noteContent").style.fontFamily =
    document.getElementById("fontStyle").value;
}

function persist() {
  try {
    localStorage.setItem(STORAGE_KEY,JSON.stringify(notes));
    return true;
  } catch(e) {
    alert("Storage is full. Export your notes and free some browser storage.");
    return false;
  }
}

function newNote() {
  editingId = null;
  document.getElementById("noteTitle").value = "";
  document.getElementById("noteContent").value = "";
  document.getElementById("pageTheme").value = "#fff0a8";
  document.getElementById("customBg").value = "#fff0a8";
  document.getElementById("fontStyle").value = "Comic Sans MS";
  document.getElementById("inkMode").value = "auto";
  updateInk();
  applyFont();
  document.getElementById("noteTitle").focus();
}

function saveNote() {
  const title = document.getElementById("noteTitle").value.trim();
  const content = document.getElementById("noteContent").value.trim();

  if(!title && !content) {
    alert("Please write something before saving!");
    return;
  }

  const note = {
    id: editingId || Date.now().toString() + Math.random(),
    title: title || "Untitled Note",
    content,
    bg: document.getElementById("customBg").value,
    page: document.getElementById("pageTheme").value,
    ink: selectedInk,
    font: document.getElementById("fontStyle").value,
    pinned: editingId
      ? (notes.find(n => n.id === editingId)?.pinned || false)
      : false,
    updated: Date.now()
  };

  if(editingId) {
    const index = notes.findIndex(n => n.id === editingId);
    if(index !== -1) notes[index] = note;
  } else {
    notes.unshift(note);
  }

  if(persist()) {
    renderNotes();
    newNote();
    alert("✨ Your sticky note has been saved!");
  }
}

function editNote(id) {
  const n = notes.find(n => n.id === id);
  if(!n) return;

  editingId = id;

  document.getElementById("noteTitle").value = n.title;
  document.getElementById("noteContent").value = n.content;
  document.getElementById("pageTheme").value = n.page;
  document.getElementById("customBg").value = n.bg;
  document.getElementById("fontStyle").value = n.font;
  document.getElementById("inkMode").value = "custom";
  document.getElementById("customInk").value = toHex(n.ink);
  updateInk();
  applyFont();

  document.getElementById("editorPanel").scrollIntoView({
    behavior:"smooth"
  });
}

function deleteNote(id) {
  if(!confirm("Delete this sticky note permanently?")) return;

  notes = notes.filter(n => n.id !== id);
  persist();
  renderNotes();
}

function pinNote(id) {
  const n = notes.find(n => n.id === id);
  if(!n) return;

  n.pinned = !n.pinned;
  persist();
  renderNotes();
}

function renderNotes() {
  const grid = document.getElementById("notesGrid");
  const search = document.getElementById("searchNotes")
    .value.toLowerCase();

  const filter = document.getElementById("filterNotes").value;
  const sort = document.getElementById("sortNotes").value;

  let filtered = notes.filter(n =>
    (n.title + " " + n.content).toLowerCase().includes(search)
  );

  if(filter === "pinned") {
    filtered = filtered.filter(n => n.pinned);
  }

  if(sort === "newest") {
    filtered.sort((a,b) => b.updated-a.updated);
  }

  if(sort === "oldest") {
    filtered.sort((a,b) => a.updated-b.updated);
  }

  if(sort === "pinned") {
    filtered.sort((a,b) => Number(b.pinned)-Number(a.pinned));
  }

  if(sort === "az") {
    filtered.sort((a,b) => a.title.localeCompare(b.title));
  }

  grid.innerHTML = "";

  filtered.forEach((n,i) => {
    const card = document.createElement("article");
    card.className = "note";

    card.style.setProperty("--note-bg",n.bg);
    card.style.setProperty("--note-ink",n.ink);
    card.style.setProperty("--rotation",
      (i%2 ? "1deg" : "-1deg"));

    const pin = document.createElement("span");
    pin.className = "pin";
    pin.textContent = n.pinned ? "📌" : "📍";
    pin.title = "Pin or unpin";
    pin.onclick = () => pinNote(n.id);

    const heading = document.createElement("h3");
    heading.textContent = n.title;
    heading.style.fontFamily = n.font;

    const body = document.createElement("p");
    body.textContent = n.content;
    body.style.fontFamily = n.font;

    const date = document.createElement("small");
    date.textContent = new Date(n.updated).toLocaleString();

    const actions = document.createElement("div");
    actions.className = "note-tools";

    const edit = document.createElement("button");
    edit.textContent = "✏ Edit";
    edit.onclick = () => editNote(n.id);

    const del = document.createElement("button");
    del.textContent = "🗑 Delete";
    del.onclick = () => deleteNote(n.id);

    const copy = document.createElement("button");
    copy.textContent = "📋 Copy";
    copy.onclick = async () => {
      try {
        await navigator.clipboard.writeText(
          n.title + "\n\n" + n.content
        );
        alert("Note copied!");
      } catch(e) {
        alert("Clipboard unavailable in this browser.");
      }
    };

    actions.append(edit,copy,del);
    card.append(pin,heading,body,date,actions);
    grid.appendChild(card);
  });

  document.getElementById("emptyMessage").style.display =
    filtered.length ? "none" : "block";

  document.getElementById("totalNotes").textContent = notes.length;
  document.getElementById("savedNotes").textContent = notes.length;
  document.getElementById("pinnedNotes").textContent =
    notes.filter(n=>n.pinned).length;
}

function showLibrary() {
  document.getElementById("notesGrid").scrollIntoView({
    behavior:"smooth"
  });
}

function clearSearch() {
  document.getElementById("searchNotes").value = "";
  document.getElementById("filterNotes").value = "all";
  renderNotes();
}

function exportNotes() {
  const blob = new Blob(
    [JSON.stringify(notes,null,2)],
    {type:"application/json"}
  );

  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url;
  a.download = "Akash_Neon_Sticky_Notes.json";
  a.click();
  URL.revokeObjectURL(url);
}

function importNotes(event) {
  const file = event.target.files[0];
  if(!file) return;

  const reader = new FileReader();

  reader.onload = () => {
    try {
      const imported = JSON.parse(reader.result);

      if(!Array.isArray(imported) ||
         !imported.every(n =>
           n && typeof n === "object" &&
           typeof n.title === "string" &&
           typeof n.content === "string" &&
           typeof n.id === "string" &&
           /^#[0-9a-f]{6}$/i.test(n.bg) &&
           /^#[0-9a-f]{6}$/i.test(n.page) &&
           /^#[0-9a-f]{6}$/i.test(n.ink)
         )) {
        throw new Error("Invalid note format");
      }

      const existing = new Set(notes.map(n=>n.id));
      const additions = imported
        .filter(n=>!existing.has(n.id))
        .map(n=>({
          ...n,
          font: typeof n.font === "string" ? n.font : "Comic Sans MS",
          pinned: !!n.pinned,
          updated: Number(n.updated) || Date.now()
        }));

      if(additions.length === 0) {
        alert("No new notes found in this backup.");
        return;
      }

      notes = [...additions,...notes];

      if(persist()) {
        renderNotes();
        alert(additions.length + " notes imported successfully!");
      }
    } catch(e) {
      alert("Invalid backup file.");
    }

    event.target.value = "";
  };

  reader.readAsText(file);
}

// Start application

generateColors();
updateInk();
renderNotes();
</script>

</body>
</html>
