# SMOKEY_PUTNUM
```react
import React, { useState, useEffect } from 'react';

// Reusable SVG Icon Components for a premium look without external dependencies
const Icons = {
  Home: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6" />
    </svg>
  ),
  Layout: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M4 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2V6zM14 6a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2V6zM4 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2H6a2 2 0 01-2-2v-2zM14 16a2 2 0 012-2h2a2 2 0 012 2v2a2 2 0 01-2 2h-2a2 2 0 01-2-2v-2z" />
    </svg>
  ),
  CheckCircle: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
  ),
  Clock: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M12 8v4l3 3m6-3a9 9 0 11-18 0 9 9 0 0118 0z" />
    </svg>
  ),
  Plus: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M12 4v16m8-8H4" />
    </svg>
  ),
  Trash: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16" />
    </svg>
  ),
  Menu: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M4 6h16M4 12h16M4 18h16" />
    </svg>
  ),
  Bell: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" />
    </svg>
  ),
  Search: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" />
    </svg>
  ),
  Kanban: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M9 17V7m0 10a2 2 0 01-2 2H5a2 2 0 01-2-2V7a2 2 0 012-2h2a2 2 0 012 2m0 10a2 2 0 002 2h2a2 2 0 002-2M9 7a2 2 0 012-2h2a2 2 0 012 2m0 10V7m0 10a2 2 0 002 2h2a2 2 0 002-2V7a2 2 0 00-2-2h-2a2 2 0 00-2 2" />
    </svg>
  ),
  Settings: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M10.325 4.317c.426-1.756 2.924-1.756 3.35 0a1.724 1.724 0 002.573 1.066c1.543-.94 3.31.826 2.37 2.37a1.724 1.724 0 001.065 2.572c1.756.426 1.756 2.924 0 3.35a1.724 1.724 0 00-1.066 2.573c.94 1.543-.826 3.31-2.37 2.37a1.724 1.724 0 00-2.572 1.065c-.426 1.756-2.924 1.756-3.35 0a1.724 1.724 0 00-2.573-1.066c-1.543.94-3.31-.826-2.37-2.37a1.724 1.724 0 00-1.065-2.572c-1.756-.426-1.756-2.924 0-3.35a1.724 1.724 0 001.066-2.573c-.94-1.543.826-3.31 2.37-2.37.996.608 2.296.07 2.572-1.065z" />
      <path strokeLinecap="round" strokeLinejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
    </svg>
  ),
  User: ({ className }) => (
    <svg className={className} fill="none" viewBox="0 0 24 24" stroke="currentColor" strokeWidth={2}>
      <path strokeLinecap="round" strokeLinejoin="round" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
    </svg>
  )
};

export default function StratumApp() {
  const [sidebarOpen, setSidebarOpen] = useState(false);
  const [currentPage, setCurrentPage] = useState('dashboard');
  
  const [tasks, setTasks] = useState([
    { id: 1, title: 'Finalize presentation slides', status: 'in-progress', priority: 'High', date: 'Today' },
    { id: 2, title: 'Review Q3 financial report', status: 'completed', priority: 'Medium', date: 'Yesterday' },
    { id: 3, title: 'Update homepage copy', status: 'todo', priority: 'Low', date: 'Tomorrow' },
    { id: 4, title: 'Weekly team sync', status: 'todo', priority: 'Medium', date: 'Today' },
    { id: 5, title: 'Design system updates', status: 'in-progress', priority: 'High', date: 'Next Week' },
  ]);
  const [newTaskTitle, setNewTaskTitle] = useState('');

  const totalTasks = tasks.length;
  const completedTasks = tasks.filter(t => t.status === 'completed').length;
  const inProgressTasks = tasks.filter(t => t.status === 'in-progress').length;
  const todoTasks = tasks.filter(t => t.status === 'todo').length;

  const toggleTaskStatus = (id) => {
    setTasks(tasks.map(task => {
      if (task.id === id) {
        const newStatus = task.status === 'completed' ? 'todo' : 'completed';
        return { ...task, status: newStatus };
      }
      return task;
    }));
  };

  const changeTaskStatus = (id, newStatus) => {
    setTasks(tasks.map(task => 
      task.id === id ? { ...task, status: newStatus } : task
    ));
  };

  const deleteTask = (id) => {
    setTasks(tasks.filter(task => task.id !== id));
  };

  const handleAddTask = (e) => {
    e.preventDefault();
    if (!newTaskTitle.trim()) return;
    
    const newTask = {
      id: Date.now(),
      title: newTaskTitle,
      status: 'todo',
      priority: 'Medium',
      date: 'Just now'
    };
    
    setTasks([newTask, ...tasks]);
    setNewTaskTitle('');
  };

  const Sidebar = () => (
    <>
      {sidebarOpen && (
        <div 
          className="fixed inset-0 bg-slate-900/50 z-40 lg:hidden transition-opacity"
          onClick={() => setSidebarOpen(false)}
        />
      )}
      
      <aside className={`
        fixed inset-y-0 left-0 z-50 w-64 bg-white border-r border-slate-200 transform transition-transform duration-300 ease-in-out lg:translate-x-0 lg:static lg:inset-0
        ${sidebarOpen ? 'translate-x-0' : '-translate-x-full'}
      `}>
        <div className="flex flex-col h-full">
          <div className="flex items-center justify-center h-20 border-b border-slate-100 px-6">
            <div className="flex items-center gap-3 w-full">
              <div className="w-8 h-8 bg-indigo-600 rounded-lg flex items-center justify-center shadow-indigo-200 shadow-lg">
                <Icons.Layout className="w-5 h-5 text-white" />
              </div>
              <span className="text-2xl font-bold text-slate-800 tracking-tight">Stratum</span>
            </div>
          </div>
          
          <nav className="flex-1 px-4 py-6 space-y-2 overflow-y-auto">
            <button 
              onClick={() => { setCurrentPage('dashboard'); setSidebarOpen(false); }}
              className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl font-medium transition-colors ${
                currentPage === 'dashboard' ? 'bg-indigo-50 text-indigo-700' : 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'
              }`}
            >
              <Icons.Home className="w-5 h-5" />
              Dashboard
            </button>
            <button 
              onClick={() => { setCurrentPage('board'); setSidebarOpen(false); }}
              className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl font-medium transition-colors ${
                currentPage === 'board' ? 'bg-indigo-50 text-indigo-700' : 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'
              }`}
            >
              <Icons.Kanban className="w-5 h-5" />
              Project Board
            </button>
            <button 
              onClick={() => { setCurrentPage('settings'); setSidebarOpen(false); }}
              className={`w-full flex items-center gap-3 px-4 py-3 rounded-xl font-medium transition-colors ${
                currentPage === 'settings' ? 'bg-indigo-50 text-indigo-700' : 'text-slate-600 hover:bg-slate-50 hover:text-slate-900'
              }`}
            >
              <Icons.Settings className="w-5 h-5" />
              Settings
            </button>
          </nav>
          
          <div className="p-4 border-t border-slate-100">
            <div className="flex items-center gap-3 px-4 py-3 bg-slate-50 rounded-xl cursor-pointer hover:bg-slate-100 transition-colors">
              <img 
                src="https://placehold.co/100x100/4f46e5/ffffff?text=AM" 
                alt="User Avatar" 
                className="w-10 h-10 rounded-full border-2 border-white shadow-sm"
              />
              <div className="flex flex-col text-left">
                <span className="text-sm font-semibold text-slate-900">Alex Morgan</span>
                <span className="text-xs text-slate-500">Workspace Admin</span>
              </div>
            </div>
          </div>
        </div>
      </aside>
    </>
  );

  const Header = () => {
    const pageTitles = {
      'dashboard': 'Overview',
      'board': 'Project Board',
      'settings': 'Account Settings'
    };

    return (
      <header className="bg-white border-b border-slate-200 sticky top-0 z-30">
        <div className="flex items-center justify-between px-4 sm:px-6 lg:px-8 h-20">
          <div className="flex items-center gap-4">
            <button 
              onClick={() => setSidebarOpen(true)}
              className="p-2 -ml-2 text-slate-600 hover:bg-slate-100 rounded-lg lg:hidden"
            >
              <Icons.Menu className="w-6 h-6" />
            </button>
            <h1 className="text-2xl font-bold text-slate-900 hidden sm:block">{pageTitles[currentPage]}</h1>
          </div>
          
          <div className="flex items-center gap-4 sm:gap-6">
            <div className="hidden md:flex items-center relative">
              <Icons.Search className="w-5 h-5 text-slate-400 absolute left-3" />
              <input 
                type="text" 
                placeholder="Search Stratum..." 
                className="pl-10 pr-4 py-2 bg-slate-100 border-transparent rounded-full text-sm focus:bg-white focus:border-indigo-500 focus:ring-2 focus:ring-indigo-200 outline-none transition-all w-64"
              />
            </div>
            <button className="p-2 text-slate-400 hover:text-indigo-600 transition-colors relative">
              <Icons.Bell className="w-6 h-6" />
              <span className="absolute top-1.5 right-2 w-2 h-2 bg-red-500 rounded-full border-2 border-white"></span>
            </button>
          </div>
        </div>
      </header>
    );
  };

  const StatCard = ({ title, value, icon, colorClass, subtitle }) => (
    <div className="bg-white p-6 rounded-2xl border border-slate-100 shadow-sm hover:shadow-md transition-shadow">
      <div className="flex items-center justify-between mb-4">
        <h3 className="text-sm font-medium text-slate-500">{title}</h3>
        <div className={`p-2 rounded-lg ${colorClass}`}>
          {icon}
        </div>
      </div>
      <div className="flex items-baseline gap-2">
        <span className="text-3xl font-bold text-slate-900">{value}</span>
        {subtitle && <span className="text-sm font-medium text-slate-500">{subtitle}</span>}
      </div>
    </div>
  );

  const DashboardView = () => (
    <div className="space-y-8 animate-in fade-in duration-500">
      <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 sm:gap-6">
        <StatCard 
          title="Total Tasks" 
          value={totalTasks} 
          icon={<Icons.Layout className="w-5 h-5" />}
          colorClass="bg-blue-50 text-blue-600"
        />
        <StatCard 
          title="To Do" 
          value={todoTasks} 
          icon={<Icons.CheckCircle className="w-5 h-5" />}
          colorClass="bg-slate-50 text-slate-600"
        />
        <StatCard 
          title="In Progress" 
          value={inProgressTasks} 
          icon={<Icons.Clock className="w-5 h-5" />}
          colorClass="bg-amber-50 text-amber-600"
        />
        <StatCard 
          title="Completed" 
          value={completedTasks} 
          subtitle={`/ ${totalTasks}`}
          icon={<Icons.CheckCircle className="w-5 h-5" />}
          colorClass="bg-emerald-50 text-emerald-600"
        />
      </div>

      <div className="bg-white rounded-2xl border border-slate-100 shadow-sm overflow-hidden">
        <div className="p-6 border-b border-slate-100">
          <h2 className="text-lg font-bold text-slate-900 mb-4">Quick Add Task</h2>
          
          <form onSubmit={handleAddTask} className="flex gap-3">
            <div className="flex-1 relative">
              <input 
                type="text" 
                value={newTaskTitle}
                onChange={(e) => setNewTaskTitle(e.target.value)}
                placeholder="What needs to be done?" 
                className="w-full pl-4 pr-4 py-3 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:bg-white focus:border-indigo-500 focus:ring-2 focus:ring-indigo-100 outline-none transition-all"
              />
            </div>
            <button 
              type="submit"
              disabled={!newTaskTitle.trim()}
              className="flex items-center justify-center gap-2 px-6 py-3 bg-indigo-600 hover:bg-indigo-700 disabled:opacity-50 disabled:cursor-not-allowed text-white font-medium rounded-xl transition-colors"
            >
              <Icons.Plus className="w-5 h-5" />
              <span className="hidden sm:inline">Add</span>
            </button>
          </form>
        </div>

        <ul className="divide-y divide-slate-100">
          {tasks.length === 0 ? (
            <li className="p-8 text-center text-slate-500">
              No tasks right now. Enjoy your day!
            </li>
          ) : (
            tasks.slice(0, 5).map((task) => (
              <li key={task.id} className="p-4 hover:bg-slate-50 transition-colors flex items-center justify-between group">
                <div className="flex items-center gap-4 flex-1 min-w-0">
                  <button 
                    onClick={() => toggleTaskStatus(task.id)}
                    className={`flex-shrink-0 w-6 h-6 rounded-full border-2 flex items-center justify-center transition-colors ${
                      task.status === 'completed' 
                        ? 'bg-emerald-500 border-emerald-500' 
                        : 'border-slate-300 hover:border-indigo-500'
                    }`}
                  >
                    {task.status === 'completed' && <Icons.CheckCircle className="w-4 h-4 text-white" />}
                  </button>
                  
                  <div className="flex flex-col min-w-0">
                    <span className={`text-sm font-medium truncate ${
                      task.status === 'completed' ? 'text-slate-400 line-through' : 'text-slate-900'
                    }`}>
                      {task.title}
                    </span>
                    <span className="text-xs text-slate-500 mt-0.5">{task.date} • {task.status.replace('-', ' ')}</span>
                  </div>
                </div>
                
                <div className="flex items-center gap-3 opacity-0 group-hover:opacity-100 transition-opacity">
                  <span className={`px-2.5 py-1 text-xs font-medium rounded-full ${
                    task.priority === 'High' ? 'bg-red-50 text-red-600' : 
                    task.priority === 'Medium' ? 'bg-amber-50 text-amber-600' : 
                    'bg-emerald-50 text-emerald-600'
                  }`}>
                    {task.priority}
                  </span>
                  <button 
                    onClick={() => deleteTask(task.id)}
                    className="p-2 text-slate-400 hover:text-red-500 hover:bg-red-50 rounded-lg transition-colors"
                  >
                    <Icons.Trash className="w-4 h-4" />
                  </button>
                </div>
              </li>
            ))
          )}
        </ul>
      </div>
    </div>
  );

  const BoardColumn = ({ title, statusId, colorClass }) => {
    const columnTasks = tasks.filter(t => t.status === statusId);
    
    return (
      <div className="flex flex-col bg-slate-50/50 rounded-2xl border border-slate-200 p-4 min-h-[500px]">
        <div className="flex items-center justify-between mb-4 px-2">
          <h3 className="font-bold text-slate-800">{title}</h3>
          <span className={`text-xs font-bold px-2.5 py-1 rounded-full ${colorClass}`}>
            {columnTasks.length}
          </span>
        </div>
        
        <div className="space-y-3 flex-1 overflow-y-auto pr-1 pb-4">
          {columnTasks.map(task => (
            <div key={task.id} className="bg-white p-4 rounded-xl shadow-sm border border-slate-100 hover:shadow-md transition-shadow group">
              <div className="flex justify-between items-start mb-2">
                <span className={`px-2 py-0.5 text-[10px] uppercase tracking-wider font-bold rounded ${
                  task.priority === 'High' ? 'bg-red-50 text-red-600' : 
                  task.priority === 'Medium' ? 'bg-amber-50 text-amber-600' : 
                  'bg-emerald-50 text-emerald-600'
                }`}>
                  {task.priority}
                </span>
                <button onClick={() => deleteTask(task.id)} className="text-slate-300 hover:text-red-500 opacity-0 group-hover:opacity-100 transition-opacity">
                  <Icons.Trash className="w-4 h-4" />
                </button>
              </div>
              <h4 className="text-sm font-medium text-slate-900 mb-3 leading-snug">{task.title}</h4>
              
              <div className="flex items-center justify-between pt-3 border-t border-slate-50 mt-auto">
                <span className="text-xs font-medium text-slate-400 flex items-center gap-1">
                  <Icons.Clock className="w-3.5 h-3.5" />
                  {task.date}
                </span>
                
                <div className="flex gap-1.5 opacity-0 group-hover:opacity-100 transition-opacity">
                  {statusId !== 'todo' && (
                     <button 
                       onClick={() => changeTaskStatus(task.id, statusId === 'completed' ? 'in-progress' : 'todo')}
                       className="text-[11px] bg-slate-100 hover:bg-slate-200 text-slate-600 px-2 py-1 rounded font-medium transition-colors"
                     >
                       Prev
                     </button>
                  )}
                  {statusId !== 'completed' && (
                     <button 
                       onClick={() => changeTaskStatus(task.id, statusId === 'todo' ? 'in-progress' : 'completed')}
                       className="text-[11px] bg-indigo-50 hover:bg-indigo-100 text-indigo-700 px-2 py-1 rounded font-medium transition-colors"
                     >
                       Next
                     </button>
                  )}
                </div>
              </div>
            </div>
          ))}
          {columnTasks.length === 0 && (
            <div className="border-2 border-dashed border-slate-200 rounded-xl h-24 flex items-center justify-center text-sla