<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Chat App</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f5f5f5; margin: 0; display: flex; justify-content: center; align-items: center; height: 100vh; }
    #app { width: 100%; max-width: 400px; background: #fff; border-radius: 12px; box-shadow: 0 0 10px rgba(0,0,0,0.1); overflow: hidden; }
    header { background: #25D366; color: #fff; text-align: center; padding: 10px; font-size: 20px; }
    #login-section, #username-section, #home-section, #chat-section { display: none; flex-direction: column; padding: 20px; }
    input, button { padding: 10px; margin: 5px 0; width: 100%; border-radius: 6px; border: 1px solid #ddd; }
    button { background: #25D366; color: white; border: none; font-weight: bold; cursor: pointer; }
    #messages { height: 300px; overflow-y: auto; background: #f0f0f0; padding: 10px; margin-bottom: 10px; border-radius: 8px; }
    .message { padding: 6px 8px; margin: 5px 0; background: white; border-radius: 6px; box-shadow: 0 0 3px rgba(0,0,0,0.1); }
    .self { background: #dcf8c6; text-align: right; }
    .user-item { display: flex; justify-content: space-between; align-items: center; padding: 8px; margin: 4px 0; background: #f0f0f0; border-radius: 6px; cursor: pointer; }
    .online { color: green; font-size: 12px; }
    .offline { color: gray; font-size: 12px; }
    .follow-btn { background: #25D366; color: white; border: none; padding: 4px 6px; font-size: 12px; border-radius: 4px; cursor: pointer; }
  </style>
</head>
<body>
  <div id="app">
    <header>Chat App</header>

    <!-- Google Sign In Section -->
    <div id="login-section">
      <button onclick="loginWithGoogle()">Sign in with Google</button>
    </div>

    <!-- Username + Password Section -->
    <div id="username-section">
      <input type="text" id="username" placeholder="Enter Username">
      <input type="password" id="password" placeholder="Enter Password">
      <button onclick="saveUsernamePassword()">Save & Continue</button>
      <button onclick="manualLogin()">Login with Username</button>
    </div>

    <!-- Home Section -->
    <div id="home-section">
      <!-- ✅ Username Show -->
      <div id="currentUserName" style="font-weight:bold; margin-bottom:8px; text-align:left;"></div>

      <input type="text" id="searchInput" placeholder="Search users..." />
      <div id="userList"></div>
      <button onclick="logout()">Logout</button>
    </div>

    <!-- Chat Section -->
    <div id="chat-section">
      <div id="messages"></div>
      <input type="text" id="messageInput" placeholder="Type a message..." />
      <button onclick="sendMessage()">Send</button>
      <button onclick="backToHome()">Back</button>
    </div>
  </div>

  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";
    import { getAnalytics } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-analytics.js";
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Chat App</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f5f5f5; margin: 0; display: flex; justify-content: center; align-items: center; height: 100vh; }
    #app { width: 100%; max-width: 400px; background: #fff; border-radius: 12px; box-shadow: 0 0 10px rgba(0,0,0,0.1); overflow: hidden; }
    header { background: #25D366; color: #fff; text-align: center; padding: 10px; font-size: 20px; }
    #login-section, #username-section, #home-section, #chat-section { display: none; flex-direction: column; padding: 20px; }
    input, button { padding: 10px; margin: 5px 0; width: 100%; border-radius: 6px; border: 1px solid #ddd; }
    button { background: #25D366; color: white; border: none; font-weight: bold; cursor: pointer; }
    #messages { height: 300px; overflow-y: auto; background: #f0f0f0; padding: 10px; margin-bottom: 10px; border-radius: 8px; }
    .message { padding: 6px 8px; margin: 5px 0; background: white; border-radius: 6px; box-shadow: 0 0 3px rgba(0,0,0,0.1); }
    .self { background: #dcf8c6; text-align: right; }
    .user-item { display: flex; justify-content: space-between; align-items: center; padding: 8px; margin: 4px 0; background: #f0f0f0; border-radius: 6px; cursor: pointer; }
    .online { color: green; font-size: 12px; }
    .offline { color: gray; font-size: 12px; }
    .follow-btn { background: #25D366; color: white; border: none; padding: 4px 6px; font-size: 12px; border-radius: 4px; cursor: pointer; }
  </style>
</head>
<body>
  <div id="app">
    <header>Chat App</header>

    <!-- Google Sign In Section -->
    <div id="login-section">
      <button onclick="loginWithGoogle()">Sign in with Google</button>
    </div>

    <!-- Username + Password Section -->
    <div id="username-section">
      <input type="text" id="username" placeholder="Enter Username">
      <input type="password" id="password" placeholder="Enter Password">
      <button onclick="saveUsernamePassword()">Save & Continue</button>
      <button onclick="manualLogin()">Login with Username</button>
    </div>

    <!-- Home Section -->
    <div id="home-section">
      <!-- ✅ Username Show -->
      <div id="currentUserName" style="font-weight:bold; margin-bottom:8px; text-align:left;"></div>

      <input type="text" id="searchInput" placeholder="Search users..." />
      <div id="userList"></div>
      <button onclick="logout()">Logout</button>
    </div>

    <!-- Chat Section -->
    <div id="chat-section">
      <div id="messages"></div>
      <input type="text" id="messageInput" placeholder="Type a message..." />
      <button onclick="sendMessage()">Send</button>
      <button onclick="backToHome()">Back</button>
    </div>
  </div>

  <script type="module">
    import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";
    import { getAnalytics } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-analytics.js";
    import { getAuth, GoogleAuthProvider, signInWithPopup, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js";
    import {
      getFirestore, collection, addDoc, query, orderBy, onSnapshot, setDoc, doc,
      getDoc, updateDoc, getDocs, where, runTransaction
    } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js";

    // ---------- CONFIG ----------
    const firebaseConfig = {
      apiKey: "AIzaSyAxPxaVFHXDPAUgklyaoYg_6WqLwsYoIwU",
      authDomain: "chat-f60ad.firebaseapp.com",
      projectId: "chat-f60ad",
      storageBucket: "chat-f60ad.firebasestorage.app",
      messagingSenderId: "877501372337",
      appId: "1:877501372337:web:ded35349e93d86f2b50f90",
      measurementId: "G-B4FPT3Z9JZ"
    };

    const app = initializeApp(firebaseConfig);
    // analytics sometimes errors if not enabled - wrap to avoid breaking
    try { getAnalytics(app); } catch(e) { console.log("Analytics not available:", e.message); }

    const auth = getAuth();
    const db = getFirestore();

    // ---------- UI refs ----------
    const loginSection = document.getElementById("login-section");
    const usernameSection = document.getElementById("username-section");
    const homeSection = document.getElementById("home-section");
    const chatSection = document.getElementById("chat-section");
    const userList = document.getElementById("userList");
    const messagesDiv = document.getElementById("messages");
    const messageInput = document.getElementById("messageInput");
    const searchInput = document.getElementById("searchInput");

    let currentEmail = null;
    let currentChatUser = null;

    // ---------- Auth state ----------
    onAuthStateChanged(auth, async (user) => {
      if (user) {
        currentEmail = user.email;
        const userDoc = await getDoc(doc(db, "users", currentEmail));
        if (userDoc.exists()) {
          usernameSection.style.display = "none";
          showHomePage();
          updateOnlineStatus(true);
        } else {
          // new user (hasn't saved username yet)
          usernameSection.style.display = "flex";
          loginSection.style.display = "none";
        }
      } else {
        loginSection.style.display = "flex";
        usernameSection.style.display = "none";
        homeSection.style.display = "none";
        chatSection.style.display = "none";
      }
    });

    // ---------- Auth helpers ----------
    window.loginWithGoogle = async function () {
      const provider = new GoogleAuthProvider();
      try {
        await signInWithPopup(auth, provider);
      } catch (error) {
        alert(error.message || "Sign-in error");
      }
    };

    window.logout = async function () {
      try {
        await updateOnlineStatus(false);
      } catch (e) { /* ignore */ }
      try { await signOut(auth); } catch(e){ console.log(e); }
    };

    function updateOnlineStatus(status) {
      if (!currentEmail) return;
      return updateDoc(doc(db, "users", currentEmail), { online: status }).catch(err => {
        // if update fails (doc not exists), ignore
        console.log("Update online failed:", err.message);
      });
    }

    // ---------- Unique username logic (transaction + case-insensitive) ----------
    // We'll keep a separate collection "usernameMap" whose doc id is usernameLower (case-insensitive)
    // usernameMap doc -> { email: user's email }

    window.saveUsernamePassword = async function () {
      const usernameRaw = document.getElementById("username").value || "";
      const password = document.getElementById("password").value || "";
      const username = usernameRaw.trim();
      if (!username || !password) return alert("Enter username & password");

      const usernameLower = username.toLowerCase();

      try {
        // Use transaction to ensure uniqueness (atomic)
        await runTransaction(db, async (tx) => {
          const usernameRef = doc(db, "usernameMap", usernameLower);
          const usernameSnap = await tx.get(usernameRef);

          if (usernameSnap.exists()) {
            // already taken
            throw new Error("USERNAME_TAKEN");
          }

          const userRef = doc(db, "users", currentEmail);
          // set username mapping and user doc together atomically
          tx.set(usernameRef, { email: currentEmail });
          tx.set(userRef, {
            username,
            username_lower: usernameLower,
            password,
            online: true,
            following: []
          });
        });

        // success
        usernameSection.style.display = "none";
        showHomePage();
      } catch (err) {
        if (err && err.message === "USERNAME_TAKEN") {
          alert("❌ Username already taken! Choose another one.");
        } else {
          console.error("saveUsernamePassword error:", err);
          alert("Error saving user: " + (err.message || err));
        }
      }
    };

    // ---------- Manual login ----------
    window.manualLogin = async function () {
      const usernameRaw = document.getElementById("username").value || "";
      const password = document.getElementById("password").value || "";
      const username = usernameRaw.trim();
      if (!username || !password) return alert("Enter username & password");

      const usernameLower = username.toLowerCase();

      try {
        const userRef = doc(db, "users", currentEmail);
        const userSnap = await getDoc(userRef);
        if (!userSnap.exists()) {
          alert("No account found with this email. Please register (Save & Continue).");
          return;
        }
        const data = userSnap.data();

        // verify credentials match this email's record
        if (data.username !== username || data.password !== password) {
          alert("Invalid username or password");
          return;
        }

        // now ensure usernameMap points to this email (create if missing)
        const usernameRef = doc(db, "usernameMap", usernameLower);
        const usernameSnap = await getDoc(usernameRef);

        if (!usernameSnap.exists()) {
          // create mapping in transaction (avoid race)
          try {
            await runTransaction(db, async (tx) => {
              const s = await tx.get(usernameRef);
              if (s.exists() && s.data().email !== currentEmail) {
                throw new Error("USERNAME_TAKEN_BY_OTHER");
              }
              tx.set(usernameRef, { email: currentEmail });
            });
          } catch (e) {
            if (e.message === "USERNAME_TAKEN_BY_OTHER") {
              alert("Username is already taken by another account");
              return;
            } else {
              throw e;
            }
          }
        } else if (usernameSnap.data().email !== currentEmail) {
          alert("This username belongs to another account");
          return;
        }

        // success
        await updateDoc(userRef, { online: true });
        usernameSection.style.display = "none";
        showHomePage();
      } catch (err) {
        console.error("manualLogin error:", err);
        alert("Login error: " + (err.message || err));
      }
    };

    // ---------- Home / Users list ----------
    async function showHomePage() {
      homeSection.style.display = "flex";
      chatSection.style.display = "none";

      // show current username (or email)
      try {
        const udoc = await getDoc(doc(db, "users", currentEmail));
        if (udoc.exists()) {
          document.getElementById("currentUserName").innerText = "👤 " + (udoc.data().username || currentEmail);
        } else {
          document.getElementById("currentUserName").innerText = "👤 " + currentEmail;
        }
      } catch (e) {
        document.getElementById("currentUserName").innerText = "👤 " + currentEmail;
      }

      await loadUsers();
    }

    async function loadUsers() {
      try {
        const usersSnapshot = await getDocs(collection(db, "users"));
        userList.innerHTML = "";
        usersSnapshot.forEach(docSnap => {
          const userData = docSnap.data();
          if (docSnap.id !== currentEmail) {
            const div = document.createElement("div");
            div.className = "user-item";
            div.innerHTML = `
              <span>${userData.username || docSnap.id}
                <small class="${userData.online ? 'online' : 'offline'}">
                  ${userData.online ? 'Online' : 'Offline'}
                </small>
              </span>
              <button class="follow-btn" onclick="(function(e){ e.stopPropagation(); followUser('${docSnap.id}'); })(event)">Follow</button>
            `;
            div.onclick = () => openChat(docSnap.id);
            userList.appendChild(div);
          }
        });
      } catch (err) {
        console.error("loadUsers error:", err);
      }

      // attach search handler once (replace previous)
      searchInput.oninput = () => {
        const filter = searchInput.value.toLowerCase();
        [...userList.children].forEach(item => {
          item.style.display = item.textContent.toLowerCase().includes(filter) ? "flex" : "none";
        });
      };
    }

    window.followUser = async function (userId) {
      try {
        const userRef = doc(db, "users", currentEmail);
        const currentDataSnap = await getDoc(userRef);
        let following = currentDataSnap.exists() ? (currentDataSnap.data().following || []) : [];
        if (!following.includes(userId)) {
          following.push(userId);
          await updateDoc(userRef, { following });
          alert("You are now following this user!");
        } else {
          alert("You already follow this user.");
        }
      } catch (err) {
        console.error("followUser error:", err);
        alert("Could not follow user.");
      }
    };

    // ---------- Chat ----------
    function openChat(userId) {
      currentChatUser = userId;
      homeSection.style.display = "none";
      chatSection.style.display = "flex";
      loadMessages();
    }

    window.backToHome = function () {
      chatSection.style.display = "none";
      homeSection.style.display = "flex";
    };

    window.sendMessage = async function () {
      if (!messageInput.value.trim()) return;
      try {
        await addDoc(collection(db, "messages"), {
          text: messageInput.value,
          from: currentEmail,
          to: currentChatUser,
          timestamp: Date.now()
        });
        messageInput.value = "";
      } catch (err) {
        console.error("sendMessage error:", err);
      }
    };

    function loadMessages() {
      const q = query(collection(db, "messages"), orderBy("timestamp", "asc"));
      onSnapshot(q, snapshot => {
        messagesDiv.innerHTML = "";
        snapshot.forEach(doc => {
          const msg = doc.data();
          if ((msg.from === currentEmail && msg.to === currentChatUser) ||
              (msg.from === currentChatUser && msg.to === currentEmail)) {
            const div = document.createElement("div");
            div.className = "message" + (msg.from === currentEmail ? " self" : "");
            // show friendly username if available
            const fromLabel = (msg.from === currentEmail) ? "You" : msg.from;
            div.innerHTML = `<strong>${fromLabel}</strong><br>${msg.text}`;
            messagesDiv.appendChild(div);
          }
        });
        messagesDiv.scrollTop = messagesDiv.scrollHeight;
      });
    }
  </script>
</body>
</html>
￼Enter    import { getAuth, GoogleAuthProvider, signInWithPopup, signOut, onAuthStateChanged } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js";
    import {
      getFirestore, collection, addDoc, query, orderBy, onSnapshot, setDoc, doc,
      getDoc, updateDoc, getDocs, where, runTransaction
    } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js";

    // ---------- CONFIG ----------
    const firebaseConfig = {
      apiKey: "AIzaSyAxPxaVFHXDPAUgklyaoYg_6WqLwsYoIwU",
      authDomain: "chat-f60ad.firebaseapp.com",
      projectId: "chat-f60ad",
      storageBucket: "chat-f60ad.firebasestorage.app",
      messagingSenderId: "877501372337",
      appId: "1:877501372337:web:ded35349e93d86f2b50f90",
      measurementId: "G-B4FPT3Z9JZ"
    };

    const app = initializeApp(firebaseConfig);
    // analytics sometimes errors if not enabled - wrap to avoid breaking
    try { getAnalytics(app); } catch(e) { console.log("Analytics not available:", e.message); }

    const auth = getAuth();
    const db = getFirestore();

    // ---------- UI refs ----------
    const loginSection = document.getElementById("login-section");
    const usernameSection = document.getElementById("username-section");
    const homeSection = document.getElementById("home-section");
    const chatSection = document.getElementById("chat-section");
    const userList = document.getElementById("userList");
    const messagesDiv = document.getElementById("messages");
    const messageInput = document.getElementById("messageInput");
    const searchInput = document.getElementById("searchInput");

    let currentEmail = null;
    let currentChatUser = null;

    // ---------- Auth state ----------
    onAuthStateChanged(auth, async (user) => {
      if (user) {
        currentEmail = user.email;
        const userDoc = await getDoc(doc(db, "users", currentEmail));
        if (userDoc.exists()) {
          usernameSection.style.display = "none";
          showHomePage();
          updateOnlineStatus(true);
        } else {
          // new user (hasn't saved username yet)
          usernameSection.style.display = "flex";
          loginSection.style.display = "none";
        }
      } else {
        loginSection.style.display = "flex";
        usernameSection.style.display = "none";
        homeSection.style.display = "none";
        chatSection.style.display = "none";
      }
    });

    // ---------- Auth helpers ----------
    window.loginWithGoogle = async function () {
      const provider = new GoogleAuthProvider();
      try {
        await signInWithPopup(auth, provider);
      } catch (error) {
        alert(error.message || "Sign-in error");
      }
    };

    window.logout = async function () {
      try {
        await updateOnlineStatus(false);
      } catch (e) { /* ignore */ }
      try { await signOut(auth); } catch(e){ console.log(e); }
    };

    function updateOnlineStatus(status) {
      if (!currentEmail) return;
      return updateDoc(doc(db, "users", currentEmail), { online: status }).catch(err => {
        // if update fails (doc not exists), ignore
        console.log("Update online failed:", err.message);
      });
    }

    // ---------- Unique username logic (transaction + case-insensitive) ----------
    // We'll keep a separate collection "usernameMap" whose doc id is usernameLower (case-insensitive)
    // usernameMap doc -> { email: user's email }

    window.saveUsernamePassword = async function () {
      const usernameRaw = document.getElementById("username").value || "";
      const password = document.getElementById("password").value || "";
      const username = usernameRaw.trim();
      if (!username || !password) return alert("Enter username & password");

      const usernameLower = username.toLowerCase();

      try {
        // Use transaction to ensure uniqueness (atomic)
        await runTransaction(db, async (tx) => {
          const usernameRef = doc(db, "usernameMap", usernameLower);
          const usernameSnap = await tx.get(usernameRef);

          if (usernameSnap.exists()) {
            // already taken
            throw new Error("USERNAME_TAKEN");
    }

          const userRef = doc(db, "users", currentEmail);
          // set username mapping and user doc together atomically
          tx.set(usernameRef, { email: currentEmail });
          tx.set(userRef, {
            username,
            username_lower: usernameLower,
            password,
            online: true,
            following: []
          });
        });

        // success
        usernameSection.style.display = "none";
        showHomePage();
      } catch (err) {
        if (err && err.message === "USERNAME_TAKEN") {
          alert("❌ Username already taken! Choose another one.");
        } else {
          console.error("saveUsernamePassword error:", err);
          alert("Error saving user: " + (err.message || err));
        }
      }
    };

    // ---------- Manual login ----------
    window.manualLogin = async function () {
      const usernameRaw = document.getElementById("username").value || "";
      const password = document.getElementById("password").value || "";
      const username = usernameRaw.trim();
      if (!username || !password) return alert("Enter username & password");

      const usernameLower = username.toLowerCase();

      try {
        const userRef = doc(db, "users", currentEmail);
        const userSnap = await getDoc(userRef);
        if (!userSnap.exists()) {
          alert("No account found with this email. Please register (Save & Continue).");
          return;
        }
        const data = userSnap.data();

        // verify credentials match this email's record
        if (data.username !== username || data.password !== password) {
          alert("Invalid username or password");
          return;
        }

        // now ensure usernameMap points to this email (create if missing)
        const usernameRef = doc(db, "usernameMap", usernameLower);
        const usernameSnap = await getDoc(usernameRef);

        if (!usernameSnap.exists()) {
          // create mapping in transaction (avoid race)
          try {
            await runTransaction(db, async (tx) => {
              const s = await tx.get(usernameRef);
              if (s.exists() && s.data().email !== currentEmail) {
                throw new Error("USERNAME_TAKEN_BY_OTHER");
              }
              tx.set(usernameRef, { email: currentEmail });
            });
          } catch (e) {
            if (e.message === "USERNAME_TAKEN_BY_OTHER") {
              alert("Username is already taken by another account");
              return;
            } else {
              throw e;
            }
          }
        } else if (usernameSnap.data().email !== currentEmail) {
          alert("This username belongs to another account");
          return;
        }

        // success
        await updateDoc(userRef, { online: true });
        usernameSection.style.display = "none";
        showHomePage();
      } catch (err) {
        console.error("manualLogin error:", err);
        alert("Login error: " + (err.message || err));
      }
    };

    // ---------- Home / Users list ----------
    async function showHomePage() {
      homeSection.style.display = "flex";
      chatSection.style.display = "none";

      // show current username (or email)
      try {
        const udoc = await getDoc(doc(db, "users", currentEmail));
        if (udoc.exists()) {
          document.getElementById("currentUserName").innerText = "👤 " + (udoc.data().username || currentEmail);
        } else {
          document.getElementById("currentUserName").innerText = "👤 " + currentEmail;
        }
      } catch (e) {
        document.getElementById("currentUserName").innerText = "👤 " + currentEmail;
      }

