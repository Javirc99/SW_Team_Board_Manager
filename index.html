<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SATCOM/F-EMIDS Board Manager</title>
    <script crossorigin src="https://cdnjs.cloudflare.com/ajax/libs/react/18.2.0/umd/react.production.min.js"></script>
    <script crossorigin src="https://cdnjs.cloudflare.com/ajax/libs/react-dom/18.2.0/umd/react-dom.production.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-standalone/7.23.5/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        .custom-scrollbar::-webkit-scrollbar { width: 4px; }
        .custom-scrollbar::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 10px; }
        .dark-select { background-color: transparent; color: #93c5fd; }
        .dark-select option { background-color: #1e293b; color: white; }
        .light-select option { background-color: white; color: #0f172a; }
        
        @keyframes pulse-slow {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.5; transform: scale(1.2); }
        }
        .animate-pulse-slow { animation: pulse-slow 2s cubic-bezier(0.4, 0, 0.6, 1) infinite; }
    </style>
</head>
<body>
    <div id="root"></div>
    
    <script type="text/babel">
        const { useState, useEffect, useRef } = React;
        
        const DEFAULT_USERS = ["admin", "fjroman", "aasensiov", "fsanchog", "msrubio", "agamboa", "jaggarcia", "jgortega", "agonzalezgar", "rgimenez"];
        const BOARD_DEFS = [
            { id: 'zcu102-1', name: 'ZCU Board 1# Master', type: 'ZCU102' },
            { id: 'zcu102-2', name: 'ZCU Board #2 Slave', type: 'ZCU102' },
            { id: 'te0818-1', name: 'TE0818 Board #1', type: 'TE0818' }
        ];

        const Lock = ({ size = 20 }) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect><path d="M7 11V7a5 5 0 0 1 10 0v4"></path></svg>;
        const Unlock = ({ size = 20 }) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect><path d="M7 11V7a5 5 0 0 1 9.9-1"></path></svg>;
        const Wrench = ({ size = 20 }) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><path d="M14.7 6.3a1 1 0 0 0 0 1.4l1.6 1.6a1 1 0 0 0 1.4 0l3.77-3.77a6 6 0 0 1-7.94 7.94l-6.91 6.91a2.12 2.12 0 0 1-3-3l6.91-6.91a6 6 0 0 1 7.94-7.94l-3.76 3.76z"></path></svg>;
        const User = ({ size = 18 }) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg>;
        const Settings = ({ size = 18 }) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><circle cx="12" cy="12" r="3"></circle><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path></svg>;
        const SunMoon = ({ isDark, size = 18 }) => isDark ? (
            <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><circle cx="12" cy="12" r="5"></circle><line x1="12" y1="1" x2="12" y2="3"></line><line x1="12" y1="21" x2="12" y2="23"></line><line x1="4.22" y1="4.22" x2="5.64" y2="5.64"></line><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"></line><line x1="1" y1="12" x2="3" y2="12"></line><line x1="21" y1="12" x2="23" y2="12"></line><line x1="4.22" y1="19.78" x2="5.64" y2="18.36"></line><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"></line></svg>
        ) : (
            <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round"><path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"></path></svg>
        );

        const BoardManager = () => {
            const [boards, setBoards] = useState([]);
            const [userName, setUserName] = useState('');
            const [whitelist, setWhitelist] = useState(DEFAULT_USERS);
            const [showLogin, setShowLogin] = useState(false);
            const [showAdmin, setShowAdmin] = useState(false);
            const [isDark, setIsDark] = useState(true);
            const [autoReleaseHours, setAutoReleaseHours] = useState(8);
            const [logo, setLogo] = useState(null);
            const [newUser, setNewUser] = useState('');
            const [lastSync, setLastSync] = useState('');
            const fileInputRef = useRef(null);

            const get24Time = () => new Date().toLocaleTimeString('en-GB', { hour: '2-digit', minute: '2-digit', second: '2-digit', hour12: false });

            const loadData = () => {
                const savedBoards = localStorage.getItem('shared_board-states');
                const savedHours = localStorage.getItem('user_auto-release-cfg');
                const savedLogo = localStorage.getItem('user_custom-logo');
                const savedUser = localStorage.getItem('user_user-name');
                const savedWhitelist = localStorage.getItem('shared_user-registry');
                const savedTheme = localStorage.getItem('user_theme');
                
                if (savedLogo) setLogo(savedLogo);
                if (savedHours) setAutoReleaseHours(Number(savedHours));
                if (savedTheme !== null) setIsDark(savedTheme === 'dark');
                
                const currentWhitelist = savedWhitelist ? JSON.parse(savedWhitelist) : DEFAULT_USERS;
                setWhitelist(currentWhitelist);
                if (savedUser && currentWhitelist.includes(savedUser)) setUserName(savedUser);
                
                let currentStates = savedBoards ? JSON.parse(savedBoards) : [];
                const now = new Date().getTime();

                const updatedStates = BOARD_DEFS.map(def => {
                    const existing = currentStates.find(b => b.id === def.id);
                    if (!existing) return { ...def, locked: false, inMaintenance: false, note: '', maintainedBy: null };
                    
                    if (existing.locked && existing.lockedAt) {
                        const hoursElapsed = (now - new Date(existing.lockedAt).getTime()) / (1000 * 60 * 60);
                        if (hoursElapsed >= autoReleaseHours) return { ...def, locked: false, lockedBy: null, lockedAt: null, inMaintenance: false, note: '', maintainedBy: null };
                    }
                    return { ...existing, name: def.name };
                });
                
                setBoards(updatedStates);
                setLastSync(get24Time());
                localStorage.setItem('shared_board-states', JSON.stringify(updatedStates));
            };

            useEffect(() => {
                loadData();
                const interval = setInterval(loadData, 30000);
                return () => clearInterval(interval);
            }, [autoReleaseHours]);

            const updateStorage = (newBoards) => {
                setBoards(newBoards);
                setLastSync(get24Time());
                localStorage.setItem('shared_board-states', JSON.stringify(newBoards));
            };

            const containerClass = isDark 
                ? "min-h-screen bg-gradient-to-br from-slate-900 via-blue-900 to-slate-900 p-8 transition-colors duration-500"
                : "min-h-screen bg-gradient-to-br from-slate-100 via-blue-100 to-slate-200 p-8 transition-colors duration-500";

            const cardBase = isDark ? "bg-white/10 border-white/10" : "bg-white/80 border-slate-200 shadow-lg";
            const textMain = isDark ? "text-white" : "text-slate-900";
            const textSub = isDark ? "text-blue-200" : "text-blue-600";

            return (
                <div className={containerClass}>
                    <div className="max-w-6xl mx-auto">
                        
                        {/* Header Section */}
                        <div className={`${cardBase} backdrop-blur-lg rounded-2xl p-8 mb-6 flex flex-col md:flex-row items-center gap-6 border`}>
                            <div className="flex flex-col items-center">
                                <div onClick={() => fileInputRef.current.click()} className="cursor-pointer bg-white p-4 rounded-lg shadow-lg min-w-[180px] h-16 flex items-center justify-center relative group overflow-hidden">
                                    {logo ? <img src={logo} className="h-full object-contain"/> : <span className="text-gray-400 text-xs font-bold uppercase tracking-widest">Logo</span>}
                                    <input type="file" ref={fileInputRef} className="hidden" accept="image/*" onChange={(e) => {
                                        const reader = new FileReader();
                                        reader.onloadend = () => { setLogo(reader.result); localStorage.setItem('user_custom-logo', reader.result); };
                                        reader.readAsDataURL(e.target.files[0]);
                                    }}/>
                                </div>
                                {/* Enlarged Sync Info */}
                                <div className={`mt-4 flex items-center gap-2 font-mono ${isDark ? 'text-blue-300' : 'text-slate-600'}`}>
                                    <span className="w-2 h-2 bg-green-500 rounded-full animate-pulse-slow"></span>
                                    <span className="text-[11px] font-bold uppercase tracking-widest opacity-60">Sync:</span>
                                    <span className="text-lg font-black tracking-tight">{lastSync}</span>
                                </div>
                            </div>

                            <div className="flex-1 text-center md:text-left">
                                <h1 className={`text-4xl font-bold ${textMain}`}>SATCOM/F-EMIDS Board Manager</h1>
                                <p className={`${textSub} mt-1 italic`}>Internal Resource Tracker</p>
                            </div>

                            <div className="flex flex-col items-end gap-2">
                                <div className="flex items-center gap-2">
                                    <button onClick={() => {setIsDark(!isDark); localStorage.setItem('user_theme', !isDark ? 'dark' : 'light');}} className={`p-2 rounded-lg ${isDark ? 'bg-white/10 text-white hover:bg-white/20' : 'bg-slate-200 text-slate-700 hover:bg-slate-300'}`}>
                                        <SunMoon isDark={isDark} />
                                    </button>
                                    {userName === 'admin' && (
                                        <button onClick={() => setShowAdmin(true)} className={`p-2 rounded-lg ${isDark ? 'bg-white/10 text-white hover:bg-white/20' : 'bg-slate-200 text-slate-700 hover:bg-slate-300'}`}>
                                            <Settings />
                                        </button>
                                    )}
                                    <div className={`flex items-center gap-3 px-4 py-2 rounded-lg ${isDark ? 'bg-white/20 text-white' : 'bg-blue-600 text-white shadow-md'}`}>
                                        <User /> <span className="font-semibold">{userName || 'Guest'}</span>
                                        <button onClick={() => setShowLogin(true)} className="text-[10px] uppercase font-bold bg-white/30 px-2 py-1 rounded">Change</button>
                                    </div>
                                </div>
                                <div className={`text-[10px] uppercase font-bold flex gap-2 ${isDark ? 'text-blue-200/50' : 'text-slate-500'}`}>
                                    Auto-Release: 
                                    <select value={autoReleaseHours} onChange={(e) => { setAutoReleaseHours(Number(e.target.value)); localStorage.setItem('user_auto-release-cfg', e.target.value); }} className={`outline-none cursor-pointer font-bold ${isDark ? 'dark-select' : 'light-select'}`}>
                                        <option value="0.5">30 min</option>
                                        <option value="1">1 hour</option>
                                        <option value="2">2 hours</option>
                                        <option value="4">4 hours</option>
                                        <option value="8">8 hours</option>
                                        <option value="12">12 hours</option>
                                    </select>
                                </div>
                            </div>
                        </div>

                        {/* Boards Grid */}
                        <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
                            {boards.map(board => (
                                <div key={board.id} className={`rounded-xl p-6 border-2 transition-all ${
                                    board.inMaintenance ? 'bg-orange-500/10 border-orange-500/50' : 
                                    board.locked ? 'bg-red-500/10 border-red-500/50' : 'bg-green-500/10 border-green-500/50'
                                } ${!isDark && 'bg-white'}`}>
                                    <div className="flex justify-between items-start mb-4">
                                        <div>
                                            <h3 className={`text-xl font-bold ${textMain}`}>{board.name}</h3>
                                            <span className={`text-[10px] uppercase font-bold tracking-widest ${isDark ? 'text-blue-300/60' : 'text-blue-600'}`}>{board.type}</span>
                                        </div>
                                        {board.inMaintenance ? <Wrench className="text-orange-500" /> : board.locked ? <Lock className="text-red-500"/> : <Unlock className="text-green-500"/>}
                                    </div>
                                    <div className="mb-6 h-14 flex flex-col justify-center">
                                        {board.inMaintenance ? (
                                            <div className="text-orange-500 text-xs truncate">
                                                <div className="font-bold uppercase text-[10px]">Maint. by {board.maintainedBy}</div>
                                                <div className="italic">"{board.note}"</div>
                                            </div>
                                        ) : board.locked ? (
                                            <div className={textMain}>
                                                <div className="flex items-center gap-2 text-sm font-medium"><User size={14}/> {board.lockedBy}</div>
                                                <div className={`text-[10px] uppercase ml-6 ${isDark ? 'text-blue-200/60' : 'text-slate-500'}`}>
                                                    {new Date(board.lockedAt).toLocaleTimeString('en-GB', {hour: '2-digit', minute:'2-digit', hour12: false})}
                                                </div>
                                            </div>
                                        ) : (
                                            <span className="text-green-600 text-sm font-bold tracking-wide">● Available</span>
                                        )}
                                    </div>
                                    <div className="space-y-3">
                                        <button 
                                            disabled={board.inMaintenance || (board.locked && board.lockedBy !== userName)} 
                                            onClick={() => {
                                                if (!userName) { setShowLogin(true); return; }
                                                updateStorage(boards.map(b => b.id === board.id ? (b.locked && b.lockedBy !== userName ? (alert(`Locked by ${b.lockedBy}`), b) : { ...b, locked: !b.locked, lockedBy: !b.locked ? userName : null, lockedAt: !b.locked ? new Date().toISOString() : null }) : b));
                                            }} 
                                            className={`w-full py-3 rounded-lg font-bold text-white transition-all shadow-md ${board.inMaintenance ? 'bg-slate-400 cursor-not-allowed' : board.locked ? 'bg-red-600 hover:bg-red-700' : 'bg-green-600 hover:bg-green-700'}`}
                                        >
                                            {board.locked ? 'Release Lock' : 'Lock Board'}
                                        </button>
                                        
                                        <button 
                                            onClick={() => { 
                                                if (!userName) { setShowLogin(true); return; }
                                                if(board.inMaintenance) { 
                                                    updateStorage(boards.map(b => b.id === board.id ? {...b, inMaintenance: false, note: '', maintainedBy: null} : b)); 
                                                } else { 
                                                    const note = prompt("Maintenance Reason:"); 
                                                    if(note !== null) updateStorage(boards.map(b => b.id === board.id ? {...b, inMaintenance: true, note: note, maintainedBy: userName, locked: false, lockedBy: null} : b)); 
                                                } 
                                            }} 
                                            className={`w-full py-2 text-[10px] uppercase font-black tracking-widest border-2 rounded-lg transition-all shadow-sm ${
                                                board.inMaintenance 
                                                ? 'bg-orange-500 text-white border-orange-600 hover:bg-orange-600' 
                                                : isDark ? 'border-white/20 text-white/60 hover:text-white hover:bg-white/10' : 'border-slate-300 text-slate-500 hover:text-slate-800 hover:bg-slate-50'
                                            }`}
                                        >
                                            {board.inMaintenance ? 'End Maintenance' : 'Set Maintenance'}
                                        </button>
                                    </div>
                                </div>
                            ))}
                        </div>

                        {/* How to Use Section */}
                        <div className={`${cardBase} backdrop-blur-lg rounded-xl p-8 border`}>
                            <h2 className={`text-xl font-bold mb-4 flex items-center gap-2 ${textMain}`}><span className="bg-blue-500 w-5 h-5 rounded-full flex items-center justify-center text-[10px] text-white">?</span>How to Use</h2>
                            <div className={`grid md:grid-cols-2 gap-8 text-sm ${isDark ? 'text-blue-100/70' : 'text-slate-600'}`}>
                                <ul className="space-y-3">
                                    <li>• 01. Select your <strong>Team Member Name</strong> to interact.</li>
                                    <li>• 02. Click <strong>Lock Board</strong> to claim a resource.</li>
                                </ul>
                                <ul className="space-y-3">
                                    <li>• 03. Use <strong>Maintenance Mode</strong> for hardware changes (logs your name).</li>
                                    <li>• 04. System auto-refreshes every 30 seconds for sync.</li>
                                </ul>
                            </div>
                        </div>
                    </div>

                    {/* Popups */}
                    {showAdmin && (
                        <div className="fixed inset-0 bg-slate-950/90 backdrop-blur-md flex items-center justify-center z-[60] p-6 text-slate-900">
                            <div className="bg-white rounded-2xl p-8 max-w-md w-full shadow-2xl">
                                <div className="flex justify-between items-center mb-6">
                                    <h2 className="text-2xl font-bold">User Registry</h2>
                                    <button onClick={() => setShowAdmin(false)} className="text-slate-400 hover:text-slate-600 font-bold text-xl">✕</button>
                                </div>
                                <div className="flex gap-2 mb-6">
                                    <input value={newUser} onChange={(e) => setNewUser(e.target.value.toLowerCase())} placeholder="New username..." className="flex-1 p-2 border-2 rounded-lg outline-none focus:border-blue-500"/>
                                    <button onClick={() => { if(newUser) { const updated = [...whitelist, newUser]; setWhitelist(updated); localStorage.setItem('shared_user-registry', JSON.stringify(updated)); setNewUser(''); } }} className="px-4 py-2 bg-blue-600 text-white rounded-lg font-bold">Add</button>
                                </div>
                                <div className="grid grid-cols-2 gap-2 max-h-64 overflow-y-auto pr-2 custom-scrollbar">
                                    {whitelist.map(u => (
                                        <div key={u} className="flex justify-between items-center p-2 bg-slate-50 rounded-lg group">
                                            <span className="font-mono text-sm">{u}</span>
                                            {u !== 'admin' && <button onClick={() => { const updated = whitelist.filter(x => x !== u); setWhitelist(updated); localStorage.setItem('shared_user-registry', JSON.stringify(updated)); }} className="text-red-400 opacity-0 group-hover:opacity-100 transition-opacity">✕</button>}
                                        </div>
                                    ))}
                                </div>
                            </div>
                        </div>
                    )}

                    {showLogin && (
                        <div className="fixed inset-0 bg-slate-950/90 backdrop-blur-md flex items-center justify-center z-50 p-6 text-slate-900">
                            <div className="bg-white rounded-2xl p-8 max-w-sm w-full">
                                <h2 className="text-2xl font-bold mb-4">Select User</h2>
                                <div className="grid grid-cols-1 gap-2 max-h-64 overflow-y-auto pr-2 custom-scrollbar">
                                    {whitelist.map(user => (
                                        <button key={user} onClick={() => { setUserName(user); localStorage.setItem('user_user-name', user); setShowLogin(false); }} className="w-full p-3 bg-slate-50 hover:bg-blue-600 hover:text-white rounded-xl text-left font-semibold transition-all">{user}</button>
                                    ))}
                                </div>
                                <button onClick={() => setShowLogin(false)} className="mt-6 w-full py-2 text-slate-400 text-[10px] uppercase font-bold">Cancel</button>
                            </div>
                        </div>
                    )}
                </div>
            );
        };

        ReactDOM.render(<BoardManager />, document.getElementById('root'));
    </script>
</body>
</html>
