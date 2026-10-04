[index.html](https://github.com/user-attachments/files/33021425/index.html)
<!DOCTYPE html>
<html lang="zh-CN" data-theme="system">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>个人工作台</title>
<style>
*{box-sizing:border-box}
:root{
  --bg:#f4f5f7; --card:#ffffff; --text:#1f2328; --muted:#6b7280;
  --border:#e3e5e8; --accent:#4f7cff; --accent-soft:#eef2ff;
  --danger:#e5484d; --danger-soft:#fdebec; --warn:#b45309; --warn-soft:#fdf3e7;
  --ok:#30a46c; --ok-soft:#e8f6ef;
  --shadow:0 1px 2px rgba(16,24,40,.06);
  color-scheme:light;
}
html[data-theme="dark"]{
  --bg:#111417; --card:#1b1f24; --text:#e7e9ec; --muted:#9aa1a9;
  --border:#2a3037; --accent:#7c9bff; --accent-soft:#222b45;
  --danger:#ff6369; --danger-soft:#3a2225; --warn:#ffb224; --warn-soft:#3a2f1c;
  --ok:#4cc38a; --ok-soft:#1d3327;
  --shadow:0 1px 2px rgba(0,0,0,.4);
  color-scheme:dark;
}
@media (prefers-color-scheme: dark){
  html[data-theme="system"]{
    --bg:#111417; --card:#1b1f24; --text:#e7e9ec; --muted:#9aa1a9;
    --border:#2a3037; --accent:#7c9bff; --accent-soft:#222b45;
    --danger:#ff6369; --danger-soft:#3a2225; --warn:#ffb224; --warn-soft:#3a2f1c;
    --ok:#4cc38a; --ok-soft:#1d3327;
    --shadow:0 1px 2px rgba(0,0,0,.4);
    color-scheme:dark;
  }
}
html,body{margin:0;padding:0}
body{
  font-family:-apple-system,"Segoe UI","Microsoft YaHei","PingFang SC",system-ui,sans-serif;
  background:var(--bg); color:var(--text); font-size:14px; line-height:1.5;
  -webkit-tap-highlight-color:transparent;
}
.app{max-width:1100px;margin:0 auto;padding:16px 16px 56px;display:flex;gap:20px;align-items:flex-start}
.sidebar{
  width:210px;flex:none;position:sticky;top:16px;max-height:calc(100vh - 32px);
  overflow-y:auto;display:flex;flex-direction:column;gap:16px;padding:2px 2px 10px;
}
.main{flex:1;min-width:0}
[hidden]{display:none !important}
header.top{display:flex;flex-wrap:wrap;gap:10px;align-items:center;justify-content:space-between}
.brand h1{font-size:20px;margin:0}
.today-line{color:var(--muted);font-size:13px;margin-top:2px}
.sync-badge{font-size:12px;color:var(--muted);margin-left:6px}
.sync-badge.err{color:var(--danger)}
.cloud-field{display:flex;flex-direction:column;gap:4px;margin:8px 0}
.cloud-field label{font-size:12px;color:var(--muted)}
.lock-error{color:var(--danger);font-size:12px;margin:6px 0}
.header-btns{display:flex;gap:6px;flex-wrap:wrap}
.btn{
  font-family:inherit;font-size:13px;padding:6px 11px;border-radius:8px;cursor:pointer;
  border:1px solid var(--border);background:var(--card);color:var(--text);
}
.btn:hover{border-color:var(--accent)}
.btn.primary{background:var(--accent);border-color:var(--accent);color:#fff}
.btn.danger{color:var(--danger);border-color:var(--danger)}
.btn.ghost{border-color:transparent;background:transparent;color:var(--muted)}
.btn.small{padding:3px 9px;font-size:12px}
.card{background:var(--card);border:1px solid var(--border);border-radius:10px;box-shadow:var(--shadow)}
.banner{
  display:flex;gap:8px;align-items:center;flex-wrap:wrap;
  background:var(--accent-soft);border:1px solid var(--accent);border-radius:8px;
  padding:8px 12px;font-size:13px;margin-top:12px;
}
.quickadd{padding:12px;margin:14px 0 4px}
.qa-main{display:flex;gap:8px;align-items:center}
.qa-main input{flex:1;min-width:0}
input,select,textarea{
  font-family:inherit;font-size:14px;color:var(--text);
  background:var(--card);border:1px solid var(--border);border-radius:8px;padding:7px 10px;
}
input:focus,select:focus,textarea:focus{outline:none;border-color:var(--accent)}
textarea{resize:vertical}
.qa-extra{margin-top:10px;display:flex;flex-direction:column;gap:8px}
.qa-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(150px,1fr));gap:8px}
.qa-grid label,.qa-note{font-size:12px;color:var(--muted);display:flex;flex-direction:column;gap:4px}
.qa-note textarea{min-height:52px}
.side-nav{display:flex;flex-direction:column;gap:4px}
.side-item{
  display:flex;align-items:center;justify-content:space-between;gap:8px;
  font-family:inherit;font-size:14px;padding:8px 12px;border-radius:8px;cursor:pointer;
  background:transparent;border:1px solid transparent;color:var(--text);text-align:left;width:100%;
}
.side-item:hover{background:var(--accent-soft)}
.side-item.active{background:var(--accent);border-color:var(--accent);color:#fff;font-weight:600}
.side-item .count{font-size:12px;background:rgba(127,127,127,.18);border-radius:999px;padding:1px 8px}
.side-item.active .count{background:rgba(255,255,255,.25)}
.side-section{display:flex;flex-direction:column}
.side-head{display:flex;align-items:center;justify-content:space-between;font-size:13px;color:var(--muted);padding:0 4px;margin-bottom:6px}
.side-head-btns{display:flex;gap:4px}
.mini{
  font-family:inherit;font-size:12px;padding:3px 9px;border-radius:6px;cursor:pointer;
  border:1px solid var(--border);background:var(--card);color:var(--text);
}
.mini:hover{border-color:var(--accent)}
.side-cats{list-style:none;margin:0;padding:0;display:flex;flex-direction:column;gap:4px}
.side-cat{
  display:flex;align-items:center;gap:8px;font-size:14px;padding:7px 12px;border-radius:8px;
  cursor:pointer;color:var(--text);border:1px solid transparent;width:100%;
  font-family:inherit;text-align:left;background:transparent;
}
.side-cat:hover{background:var(--accent-soft)}
.side-cat.active{background:var(--accent-soft);border-color:var(--accent);font-weight:600}
.side-cat .dot{width:10px;height:10px;border-radius:50%;flex:none}
.side-cat .name{flex:1;min-width:0;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
.side-cat .count{font-size:12px;color:var(--muted)}
.side-hint{font-size:12px;color:var(--muted);padding:2px 12px}
.stats{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:10px}
.chip{
  background:var(--card);border:1px solid var(--border);border-radius:999px;
  padding:3px 12px;font-size:13px;color:var(--muted);
}
.chip b{color:var(--text);font-weight:600}
.chip.overdue b{color:var(--danger)}
.toolbar{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:10px}
#search{flex:1;min-width:140px}
.list{list-style:none;margin:0;padding:0;display:flex;flex-direction:column;gap:8px}
.task{
  display:flex;gap:10px;align-items:flex-start;background:var(--card);
  border:1px solid var(--border);border-radius:10px;padding:10px 12px;
  cursor:pointer;box-shadow:var(--shadow);
}
.task:hover{border-color:var(--accent)}
.task.done{opacity:.62}
.task.done .t-text{text-decoration:line-through}
.check{
  flex:none;width:22px;height:22px;margin-top:1px;border-radius:50%;
  border:2px solid var(--border);background:transparent;color:#fff;cursor:pointer;
  display:flex;align-items:center;justify-content:center;font-size:13px;line-height:1;
}
.check:hover{border-color:var(--ok)}
.task.done .check{background:var(--ok);border-color:var(--ok)}
.task-body{flex:1;min-width:0}
.task-title{display:flex;gap:6px;align-items:center;flex-wrap:wrap}
.t-text{font-size:15px;word-break:break-word}
.note-prev{
  color:var(--muted);font-size:13px;margin-top:3px;white-space:pre-wrap;word-break:break-word;
  display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;
}
.task-meta{display:flex;gap:6px;flex-wrap:wrap;margin-top:6px;align-items:center}
.badge{font-size:12px;padding:2px 8px;border-radius:6px;background:var(--accent-soft);color:var(--accent);white-space:nowrap}
.badge.due.overdue{background:var(--danger-soft);color:var(--danger)}
.badge.due.today{background:var(--warn-soft);color:var(--warn)}
.badge.prio.p-high{background:var(--danger-soft);color:var(--danger)}
.badge.prio.p-med{background:var(--warn-soft);color:var(--warn)}
.badge.prio.p-low{background:var(--accent-soft);color:var(--accent)}
.badge.cat{display:inline-flex;align-items:center;gap:5px;cursor:pointer}
.badge.cat .dot{width:8px;height:8px;border-radius:50%}
.badge.rep{background:var(--ok-soft);color:var(--ok)}
.badge.sub{background:transparent;border:1px dashed var(--border);color:var(--muted)}
.subtasks{list-style:none;margin:8px 0 0;padding:0;display:flex;flex-direction:column;gap:2px}
.sub-row{display:flex;align-items:center;gap:8px;padding:3px 6px;border-radius:6px}
.sub-row:hover{background:var(--accent-soft)}
.sub-check{
  flex:none;width:16px;height:16px;border-radius:50%;border:2px solid var(--border);
  background:transparent;color:#fff;cursor:pointer;display:flex;align-items:center;
  justify-content:center;font-size:10px;line-height:1;padding:0;
}
.sub-check:hover{border-color:var(--ok)}
.sub-row.done .sub-check{background:var(--ok);border-color:var(--ok)}
.sub-text{flex:1;min-width:0;font-size:13px;word-break:break-word}
.sub-row.done .sub-text{text-decoration:line-through;color:var(--muted)}
.sub-del{opacity:.55;font-size:12px}
.sub-del:hover{opacity:1}
.sub-add{margin-top:6px}
.sub-add-btn{
  font-family:inherit;font-size:12px;color:var(--muted);background:transparent;
  border:1px dashed var(--border);border-radius:6px;padding:3px 10px;cursor:pointer;
}
.sub-add-btn:hover{color:var(--accent);border-color:var(--accent)}
.sub-add input{width:100%;font-size:13px;padding:5px 8px}
.badge.doneat{background:transparent;color:var(--muted);border:1px solid var(--border)}
.task-actions{display:flex;gap:2px;flex:none}
.icon-btn{
  background:transparent;border:none;color:var(--muted);cursor:pointer;
  font-size:15px;padding:3px 5px;border-radius:6px;font-family:inherit;
}
.icon-btn:hover{color:var(--danger)}
.empty{text-align:center;color:var(--muted);padding:44px 16px;font-size:14px}
.empty .sub{font-size:13px;margin-top:6px;opacity:.8}
.modal-overlay{
  position:fixed;inset:0;background:rgba(0,0,0,.45);z-index:50;
  display:flex;align-items:center;justify-content:center;padding:16px;
}
.modal{
  background:var(--card);border:1px solid var(--border);border-radius:12px;
  padding:18px;width:100%;max-width:430px;max-height:86vh;overflow:auto;
  box-shadow:0 10px 40px rgba(0,0,0,.25);
}
.modal h2{margin:0 0 12px;font-size:17px}
.set-row{
  display:flex;align-items:center;justify-content:space-between;gap:10px;
  padding:7px 0;font-size:14px;flex-wrap:wrap;
}
.set-row .ctl{display:flex;align-items:center;gap:6px}
.notify-status{font-size:12px;color:var(--muted);padding:2px 0}
.cat-add{display:flex;gap:8px;margin-bottom:10px}
.cat-add input{flex:1}
.cat-list{list-style:none;margin:0;padding:0;display:flex;flex-direction:column;gap:6px}
.cat-row{display:flex;align-items:center;gap:8px}
.cat-dot{width:16px;height:16px;border-radius:50%;cursor:pointer;flex:none;border:1px solid var(--border)}
.cat-row input{flex:1}
.modal-actions{display:flex;justify-content:flex-end;gap:8px;margin-top:14px;flex-wrap:wrap}
.hint{color:var(--muted);font-size:12px;line-height:1.7;margin:6px 0 0}
hr{border:none;border-top:1px solid var(--border);margin:14px 0}
.toast{
  position:fixed;left:50%;bottom:24px;transform:translateX(-50%);
  background:#1f2328;color:#fff;padding:9px 18px;border-radius:8px;
  font-size:13px;z-index:99;box-shadow:0 6px 24px rgba(0,0,0,.3);max-width:84vw;
}
@media (max-width:760px){
  .app{flex-direction:column}
  .sidebar{
    width:100%;position:static;max-height:none;flex-direction:row;gap:12px;
    overflow-x:auto;align-items:flex-start;padding:4px 0;flex-wrap:nowrap;
  }
  .side-nav{flex-direction:row;flex:none}
  .side-item{white-space:nowrap;width:auto}
  .side-section{flex:none}
  .side-cats{flex-direction:row;gap:4px}
  .side-cat{width:auto;white-space:nowrap;padding:6px 10px}
  .side-hint{white-space:nowrap}
}
@media (max-width:560px){
  .app{padding:10px 10px 56px}
  input,select,textarea{font-size:16px}
  .qa-grid{grid-template-columns:1fr 1fr}
  .header-btns{width:100%}
  .check{width:26px;height:26px}
  .sub-check{width:20px;height:20px}
  .modal{max-width:100%}
}
</style>
</head>
<body>
<div class="app">

  <aside class="sidebar">
    <nav class="side-nav">
      <button class="side-item active" id="tabTodo">📋 待办<span class="count" id="cntTodo">0</span></button>
      <button class="side-item" id="tabDone">✅ 已完成<span class="count" id="cntDone">0</span></button>
    </nav>
    <div class="side-section">
      <div class="side-head">
        <span>🏷️ 分类</span>
        <span class="side-head-btns">
          <button class="mini" id="btnAddCatQuick" title="添加分类">＋</button>
          <button class="mini" id="btnCats" title="管理分类（改名/换色/删除）">管理</button>
        </span>
      </div>
      <ul class="side-cats" id="sideCatList"></ul>
    </div>
  </aside>

  <main class="main">

  <header class="top">
    <div class="brand">
      <h1>个人工作台</h1>
      <div class="today-line"><span id="todayText"></span><span class="sync-badge" id="syncBadge" hidden></span></div>
    </div>
    <div class="header-btns">
      <button class="btn" id="btnSync" title="把数据同步保存为 HTML 旁边的数据文件（需要 Chrome/Edge）">☁️ 数据文件</button>
      <button class="btn" id="btnExport" title="导出 JSON 备份文件">📤 导出</button>
      <button class="btn" id="btnImport" title="从 JSON 备份文件导入">📥 导入</button>
      <button class="btn" id="btnTheme" title="切换主题">🌓</button>
      <button class="btn" id="btnSettings" title="设置">⚙️</button>
    </div>
  </header>

  <div class="banner" id="syncBanner" hidden>
    <span>检测到之前连接过数据文件，点击「重新连接」即可恢复自动同步。</span>
    <button class="btn small primary" id="btnReconnect">重新连接</button>
    <button class="btn small ghost" id="bannerClose">✕</button>
  </div>

  <section class="quickadd card" id="quickAddCard">
    <div class="qa-main">
      <input id="qaTitle" type="text" placeholder="写下要办的事，回车即可添加…" autocomplete="off" maxlength="200">
      <button class="btn ghost" id="btnMore" title="更多选项">▾</button>
      <button class="btn primary" id="btnSubmit">添加</button>
      <button class="btn ghost" id="btnCancelEdit" hidden>取消</button>
    </div>
    <div class="qa-extra" id="qaExtra" hidden>
      <div class="qa-grid">
        <label>截止日期
          <input type="date" id="qaDue">
        </label>
        <label>优先级
          <select id="qaPrio">
            <option value="none">无</option>
            <option value="low">低</option>
            <option value="medium">中</option>
            <option value="high">高</option>
          </select>
        </label>
        <label>分类
          <select id="qaCat"><option value="">无分类</option></select>
        </label>
        <label>重复
          <select id="qaRepeat">
            <option value="none">不重复</option>
            <option value="daily">每天</option>
            <option value="weekly">每周</option>
            <option value="monthly">每月</option>
            <option value="yearly">每年</option>
          </select>
        </label>
      </div>
      <label class="qa-note">备注
        <textarea id="qaNote" rows="2" placeholder="选填"></textarea>
      </label>
    </div>
  </section>

  <div class="stats" id="stats"></div>

  <div class="toolbar" id="toolbar">
    <span id="filterGroup" style="display:contents">
      <input id="search" type="search" placeholder="🔍 搜索任务…" autocomplete="off">
      <select id="selFilter">
        <option value="all">全部</option>
        <option value="overdue">已过期</option>
        <option value="today">今天到期</option>
        <option value="week">本周到期</option>
        <option value="nodate">无日期</option>
      </select>
      <select id="selSort">
        <option value="smart">智能排序</option>
        <option value="due">按截止日期</option>
        <option value="priority">按优先级</option>
        <option value="created">按创建时间</option>
      </select>
    </span>
    <button class="btn ghost small" id="btnClearDone" hidden>🗑 清空已完成</button>
  </div>

  <ul class="list" id="taskList"></ul>
  <div class="empty" id="emptyState" hidden></div>

  </main>

</div>

<div class="modal-overlay" id="modalCats" hidden>
  <div class="modal">
    <h2>🏷️ 分类管理</h2>
    <div class="cat-add">
      <input id="newCatName" type="text" placeholder="新分类名称（如：工作）" maxlength="20">
      <button class="btn primary" id="btnAddCat">添加</button>
    </div>
    <ul class="cat-list" id="catList"></ul>
    <p class="hint">点击色块可换颜色；点击 🗑 删除分类（该分类下的任务会变为「无分类」，任务本身保留）。</p>
    <div class="modal-actions"><button class="btn" data-close>关闭</button></div>
  </div>
</div>

<div class="modal-overlay" id="modalSettings" hidden>
  <div class="modal">
    <h2>⚙️ 设置</h2>
    <div class="set-row">
      <span>主题</span>
      <select id="setTheme">
        <option value="system">跟随系统</option>
        <option value="light">浅色</option>
        <option value="dark">深色</option>
      </select>
    </div>
    <div class="set-row">
      <span>到期提醒（页面打开时生效）</span>
      <span class="ctl"><input type="checkbox" id="setNotify"></span>
    </div>
    <div class="set-row">
      <span>提醒提前量</span>
      <select id="setAdvance">
        <option value="0">到期当天</option>
        <option value="1">提前 1 天</option>
        <option value="3">提前 3 天</option>
      </select>
    </div>
    <div class="notify-status" id="notifyStatus"></div>
    <div class="set-row">
      <span></span>
      <button class="btn small" id="btnNotifyPerm">开启浏览器通知权限</button>
    </div>
    <hr>
    <div class="set-row">
      <span>☁️ 云同步</span>
      <span class="hint" id="cloudStatus">未配置</span>
    </div>
    <div class="cloud-field"><label>GitHub 用户名</label><input id="cfgOwner" placeholder="如 zhangsan" autocomplete="off"></div>
    <div class="cloud-field"><label>仓库名</label><input id="cfgRepo" placeholder="如 workbench" autocomplete="off"></div>
    <div class="cloud-field"><label>分支（留空用仓库默认分支）</label><input id="cfgBranch" placeholder="main" autocomplete="off"></div>
    <div class="cloud-field"><label>数据文件名</label><input id="cfgPath" placeholder="workbench-data.json" autocomplete="off"></div>
    <div class="cloud-field"><label>访问令牌 Token（只给该仓库 Contents 读写权限）</label><input id="cfgToken" type="password" placeholder="ghp_… 或 github_pat_…" autocomplete="off"></div>
    <div class="cloud-field"><label>分享链接前缀（GitHub Pages 地址，可选）</label><input id="cfgPages" placeholder="https://用户名.github.io/仓库名/" autocomplete="off"></div>
    <div class="set-row" style="justify-content:flex-start;gap:8px">
      <button class="btn small primary" id="btnSaveCloud">保存配置</button>
      <button class="btn small" id="btnShareLink">生成共享链接</button>
      <button class="btn small" id="btnCloudNow" hidden>立即同步</button>
      <button class="btn small danger" id="btnCloudOff" hidden>断开云同步</button>
    </div>
    <input id="shareLinkOut" type="text" readonly placeholder="共享链接将显示在这里" style="width:100%;font-size:12px" hidden>
    <p class="hint">数据会加密后存进你仓库的 JSON 文件，只有拿到链接并输入正确密码的人才能看到内容。⚠️ 密码忘记后云端数据无法解密找回，请务必记好密码。</p>
    <hr>
    <div class="set-row">
      <span>清空全部数据</span>
      <button class="btn small danger" id="btnClearAll">清空</button>
    </div>
    <p class="hint">
      数据默认保存在本机浏览器中（localStorage），关掉页面仍在；若浏览器清理数据会丢失。<br>
      点首页「☁️ 数据文件」可把数据同步保存成 HTML 旁边的 JSON 文件（仅 Chrome/Edge 支持），清缓存也不丢；也可用「📤 导出」手动备份、「📥 导入」恢复。
    </p>
    <div class="modal-actions"><button class="btn" data-close>关闭</button></div>
  </div>
</div>

<div class="modal-overlay" id="modalConflict" hidden>
  <div class="modal">
    <h2>数据冲突</h2>
    <p>数据文件和浏览器里都有数据，以哪边为准？</p>
    <div class="modal-actions" style="justify-content:flex-start">
      <button class="btn primary" id="btnUseFile">用文件数据（覆盖浏览器）</button>
      <button class="btn" id="btnUseLocal">用浏览器数据（覆盖文件）</button>
      <button class="btn ghost" id="btnCancelConflict">取消</button>
    </div>
  </div>
</div>

<input type="file" id="fileImport" accept=".json,application/json" hidden>

<div class="modal-overlay" id="lockScreen" hidden>
  <div class="modal lock-modal">
    <h2>🔒 共享工作台</h2>
    <p class="hint">这是共享版工作台，数据已加密存储在云端。请输入访问密码：</p>
    <input type="password" id="lockPw" placeholder="访问密码" autocomplete="current-password" style="width:100%">
    <label class="hint" style="display:flex;align-items:center;gap:6px;margin:8px 0"><input type="checkbox" id="lockRemember"> 记住密码（保存在本机浏览器）</label>
    <div class="lock-error" id="lockError" hidden></div>
    <div class="modal-actions" style="justify-content:flex-start">
      <button class="btn primary" id="btnUnlock">解锁</button>
      <button class="btn ghost" id="btnOfflineOpen">离线打开本地数据</button>
    </div>
  </div>
</div>

<div class="toast" id="toast" hidden></div>

<script>
(function(){
'use strict';

/* ================= 常量与工具 ================= */
var LS_KEY = 'workbench.data.v1';
var LS_NOTIF = 'workbench.notified.v1';
var LS_SYNC = 'workbench.syncflag.v1';
var LS_CLOUD = 'workbench.cloud.v1';
var LS_CLOUD_PW = 'workbench.cloudpw.v1';
var LS_TOMB = 'workbench.tombstones.v1';

var PRIO = {
  none:   {label:'无', rank:0, cls:'p-none'},
  low:    {label:'低', rank:1, cls:'p-low'},
  medium: {label:'中', rank:2, cls:'p-med'},
  high:   {label:'高', rank:3, cls:'p-high'}
};
var REPEAT = { none:{label:''}, daily:{label:'每天'}, weekly:{label:'每周'}, monthly:{label:'每月'}, yearly:{label:'每年'} };
var PALETTE = ['#4f7cff','#e5484d','#30a46c','#f5a623','#9b5de5','#00b3b0','#e06287','#8a7a5c'];
var THEME_LABEL = { system:'跟随系统', light:'浅色', dark:'深色' };
var THEME_ICON = { system:'🌓', light:'☀️', dark:'🌙' };
var WEEKDAY = ['周日','周一','周二','周三','周四','周五','周六'];

function qs(s){ return document.querySelector(s); }
function pad(n){ return (n<10?'0':'')+n; }
function fmtDate(d){ return d.getFullYear()+'-'+pad(d.getMonth()+1)+'-'+pad(d.getDate()); }
function todayStr(){ return fmtDate(new Date()); }
function parseDate(s){ var p=s.split('-'); return new Date(Number(p[0]),Number(p[1])-1,Number(p[2])); }
function addDays(d,n){ var r=new Date(d.getTime()); r.setDate(r.getDate()+n); return r; }
function addMonthsClamped(d,n){
  var day=d.getDate(), r=new Date(d.getFullYear(), d.getMonth()+n, 1);
  var last=new Date(r.getFullYear(), r.getMonth()+1, 0).getDate();
  r.setDate(Math.min(day,last)); return r;
}
function addYearsClamped(d,n){
  var day=d.getDate(), r=new Date(d.getFullYear()+n, d.getMonth(), 1);
  var last=new Date(r.getFullYear(), r.getMonth()+1, 0).getDate();
  r.setDate(Math.min(day,last)); return r;
}
function weekRange(){
  var t=new Date(), dow=(t.getDay()+6)%7;
  var mon=addDays(t,-dow), sun=addDays(mon,6);
  return { mon:fmtDate(mon), sun:fmtDate(sun) };
}
function uid(){ return Date.now().toString(36)+Math.random().toString(36).slice(2,8); }
function rankPrio(p){ return (PRIO[p]?PRIO[p].rank:0); }

/* ================= 数据 ================= */
var state = null;
var fileHandle = null;
var editingId = null;
var ui = { tab:'todo', filter:'all', cat:'', sort:'smart', q:'' };
var cloud = { cfg:null, key:null, enabled:false, lastSha:null, lastSync:0, dirty:false, dirtySeq:0, pushing:false, pollTimer:null, pushTimer:null };

function defaultState(){
  return { version:1, tasks:[], categories:[], settings:{ theme:'system', notify:false, advance:'0' } };
}
function normalize(s){
  var tasks = [];
  if(Array.isArray(s.tasks)){
    tasks = s.tasks.map(function(t){
      return {
        id:String(t.id||uid()),
        title:String(t.title||''),
        note:String(t.note||''),
        due:(typeof t.due==='string' && /^\d{4}-\d{2}-\d{2}$/.test(t.due))?t.due:null,
        priority:['high','medium','low','none'].indexOf(t.priority)>=0?t.priority:'none',
        categoryId:t.categoryId||null,
        repeat:['daily','weekly','monthly','yearly','none'].indexOf(t.repeat)>=0?t.repeat:'none',
        done:!!t.done,
        createdAt:Number(t.createdAt)||Date.now(),
        completedAt:Number(t.completedAt)||null,
        updatedAt:Number(t.updatedAt)||Date.now(),
        subtasks:Array.isArray(t.subtasks)?t.subtasks.map(function(st){
          return {
            id:String(st.id||uid()),
            title:String(st.title||''),
            done:!!st.done,
            createdAt:Number(st.createdAt)||Date.now(),
            completedAt:Number(st.completedAt)||null
          };
        }).filter(function(st){ return st.title; }):[]
      };
    }).filter(function(t){ return t.title; });
  }
  var cats = [];
  if(Array.isArray(s.categories)){
    cats = s.categories.map(function(c){
      return {
        id:String(c.id||uid()),
        name:String(c.name||''),
        color:/^#[0-9a-fA-F]{6}$/.test(c.color)?c.color:PALETTE[0],
        updatedAt:Number(c.updatedAt)||Date.now()
      };
    }).filter(function(c){ return c.name; });
  }
  return {
    version:1,
    tasks:tasks,
    categories:cats,
    settings:Object.assign({theme:'system',notify:false,advance:'0'}, s.settings||{})
  };
}
function loadState(){
  try{
    var raw=localStorage.getItem(LS_KEY);
    if(raw){
      var s=JSON.parse(raw);
      if(s && Array.isArray(s.tasks)){ state=normalize(s); return; }
    }
  }catch(e){}
  state=defaultState();
}
function scheduleFileWrite(){
  if(!fileHandle) return;
  if(window.__wbWriteTimer) clearTimeout(window.__wbWriteTimer);
  window.__wbWriteTimer=setTimeout(writeFileNow,400);
}
function saveState(){
  try{ localStorage.setItem(LS_KEY, JSON.stringify(state)); }
  catch(e){ toast('保存到浏览器失败：'+e.message); }
  scheduleFileWrite();
  if(cloud.enabled){ cloud.dirty=true; cloud.dirtySeq++; schedulePush(900); }
}
function saveLocal(){
  try{ localStorage.setItem(LS_KEY, JSON.stringify(state)); }catch(e){}
  scheduleFileWrite();
}

/* ================= 通知提醒 ================= */
function loadNotified(){
  try{ var r=JSON.parse(localStorage.getItem(LS_NOTIF)||'{}'); return (r&&typeof r==='object')?r:{}; }catch(e){ return {}; }
}
var notified = loadNotified();
function saveNotified(){
  try{ localStorage.setItem(LS_NOTIF, JSON.stringify(notified)); }catch(e){}
}
function loadTombstones(){
  try{ var r=JSON.parse(localStorage.getItem(LS_TOMB)||'{}'); return (r&&typeof r==='object')?r:{}; }catch(e){ return {}; }
}
var tombstones = loadTombstones();
function saveTombstones(){
  try{ localStorage.setItem(LS_TOMB, JSON.stringify(tombstones)); }catch(e){}
}
function addTombstone(k){
  tombstones[k]=Date.now();
  saveTombstones();
}
(function pruneOldTombstones(){
  var cut=Date.now()-30*86400000;
  var keys=Object.keys(tombstones), ch=false;
  for(var i=0;i<keys.length;i++){ if(tombstones[keys[i]]<cut){ delete tombstones[keys[i]]; ch=true; } }
  if(ch) saveTombstones();
})();
function checkReminders(){
  if(!state || !state.settings.notify) return;
  if(!('Notification' in window) || Notification.permission!=='granted') return;
  var today=todayStr();
  var cut=fmtDate(addDays(new Date(), parseInt(state.settings.advance,10)||0));
  var changed=false;
  for(var i=0;i<state.tasks.length;i++){
    var t=state.tasks[i];
    if(t.done || !t.due || t.due>cut) continue;
    if(notified[t.id]===today) continue;
    notified[t.id]=today; changed=true;
    var body;
    if(t.due===today) body='今天到期：'+t.title;
    else if(t.due<today) body='已过期：'+t.title+'（'+t.due+'）';
    else body='即将到期：'+t.title+'（'+t.due+'）';
    try{ new Notification('📌 任务提醒', { body:body }); }catch(e){}
  }
  if(changed){
    var weekAgo=fmtDate(addDays(new Date(),-7));
    var keys=Object.keys(notified);
    for(var k=0;k<keys.length;k++){ if(notified[keys[k]]<weekAgo) delete notified[keys[k]]; }
    saveNotified();
  }
}

/* ================= 主题 ================= */
function applyTheme(){ document.documentElement.setAttribute('data-theme', state.settings.theme||'system'); }

/* ================= 分类 ================= */
function findCat(id){
  for(var i=0;i<state.categories.length;i++){ if(state.categories[i].id===id) return state.categories[i]; }
  return null;
}
function nextCatColor(){ return PALETTE[state.categories.length % PALETTE.length]; }

/* ================= 任务操作 ================= */
function spawnNext(t){
  var base = t.due ? parseDate(t.due) : new Date();
  var next = new Date(base.getTime());
  var today = parseDate(todayStr());
  var guard=0;
  do{
    if(t.repeat==='daily') next=addDays(next,1);
    else if(t.repeat==='weekly') next=addDays(next,7);
    else if(t.repeat==='monthly') next=addMonthsClamped(next,1);
    else next=addYearsClamped(next,1);
    guard++;
    if(guard>10000){ next=addDays(new Date(),1); break; }
  } while(next<=today);
  state.tasks.push({
    id:uid(), title:t.title, note:t.note, due:fmtDate(next),
    priority:t.priority, categoryId:t.categoryId, repeat:t.repeat,
    done:false, createdAt:Date.now(), completedAt:null, updatedAt:Date.now(),
    subtasks:(t.subtasks||[]).map(function(st){
      return {id:uid(), title:st.title, done:false, createdAt:Date.now(), completedAt:null};
    })
  });
}
function completeTask(id){
  var t=null;
  for(var i=0;i<state.tasks.length;i++){ if(state.tasks[i].id===id){ t=state.tasks[i]; break; } }
  if(!t || t.done) return;
  t.done=true; t.completedAt=Date.now(); t.updatedAt=Date.now();
  if(t.subtasks){
    for(var si=0;si<t.subtasks.length;si++){
      if(!t.subtasks[si].done){ t.subtasks[si].done=true; t.subtasks[si].completedAt=Date.now(); }
    }
  }
  if(t.repeat && t.repeat!=='none') spawnNext(t);
  saveState(); render();
}
function restoreTask(id){
  var t=null;
  for(var i=0;i<state.tasks.length;i++){ if(state.tasks[i].id===id){ t=state.tasks[i]; break; } }
  if(!t) return;
  t.done=false; t.completedAt=null; t.updatedAt=Date.now();
  saveState(); render();
}
function removeTask(id){
  if(!confirm('确定删除这条任务？删除后不可恢复。')) return;
  state.tasks=state.tasks.filter(function(t){ return t.id!==id; });
  addTombstone('t:'+id);
  saveState(); render();
}
function clearDone(){
  if(!confirm('确定清空「已完成」里的全部任务？')) return;
  state.tasks.filter(function(t){ return t.done; }).forEach(function(t){ addTombstone('t:'+t.id); });
  state.tasks=state.tasks.filter(function(t){ return !t.done; });
  saveState(); render();
}

/* ================= 排序与筛选 ================= */
function overdueRank(t){
  var today=todayStr();
  if(t.due && t.due<today) return 0;
  if(t.due) return 1;
  return 2;
}
function cmpSmart(a,b){
  var x=overdueRank(a), y=overdueRank(b);
  if(x!==y) return x-y;
  if(a.due||b.due){
    if(a.due&&b.due&&a.due!==b.due) return a.due<b.due?-1:1;
    if(a.due&&!b.due) return -1;
    if(!a.due&&b.due) return 1;
  }
  var pr=rankPrio(b.priority)-rankPrio(a.priority);
  if(pr) return pr;
  return (a.createdAt||0)-(b.createdAt||0);
}
function cmpDue(a,b){
  if(a.due&&b.due&&a.due!==b.due) return a.due<b.due?-1:1;
  if(a.due&&!b.due) return -1;
  if(!a.due&&b.due) return 1;
  var pr=rankPrio(b.priority)-rankPrio(a.priority);
  if(pr) return pr;
  return (a.createdAt||0)-(b.createdAt||0);
}
function cmpPrio(a,b){
  var pr=rankPrio(b.priority)-rankPrio(a.priority);
  if(pr) return pr;
  return cmpDue(a,b);
}
function cmpCreated(a,b){ return (a.createdAt||0)-(b.createdAt||0); }
function matchFilter(t){
  if(ui.cat && t.categoryId!==ui.cat) return false;
  if(ui.q){
    var q=ui.q.toLowerCase();
    var hay=t.title+' '+(t.note||'');
    if(t.subtasks){ for(var si=0;si<t.subtasks.length;si++){ hay+=' '+t.subtasks[si].title; } }
    if(hay.toLowerCase().indexOf(q)<0) return false;
  }
  var today=todayStr(), wr=weekRange();
  switch(ui.filter){
    case 'overdue': return !!t.due && t.due<today;
    case 'today':   return t.due===today;
    case 'week':    return !!t.due && t.due>today && t.due<=wr.sun;
    case 'nodate':  return !t.due;
  }
  return true;
}

/* ================= 渲染 ================= */
function dueInfo(due){
  var today=todayStr();
  var tmr=fmtDate(addDays(new Date(),1));
  var wr=weekRange();
  if(due<today) return {label:'已过期', cls:'overdue'};
  if(due===today) return {label:'今天', cls:'today'};
  if(due===tmr) return {label:'明天', cls:''};
  var d=parseDate(due), now=new Date();
  var label=(d.getFullYear()===now.getFullYear()?'':d.getFullYear()+'年')+(d.getMonth()+1)+'月'+d.getDate()+'日';
  if(due<=wr.sun) label='本周 · '+label;
  return {label:label, cls:''};
}
function fillCatSelect(sel, placeholder){
  var prev=sel.value;
  sel.innerHTML='';
  var o0=document.createElement('option');
  o0.value=''; o0.textContent=placeholder;
  sel.appendChild(o0);
  for(var i=0;i<state.categories.length;i++){
    var c=state.categories[i], o=document.createElement('option');
    o.value=c.id; o.textContent=c.name;
    sel.appendChild(o);
  }
  var found=state.categories.some(function(c){ return c.id===prev; });
  sel.value=found?prev:'';
}
function renderHeader(){
  var d=new Date();
  qs('#todayText').textContent='今天 · '+(d.getMonth()+1)+'月'+d.getDate()+'日 '+WEEKDAY[d.getDay()];
}
function renderStats(){
  var today=todayStr(), wr=weekRange();
  var pending=0, overdue=0, todayDone=0, weekDone=0, doneCount=0;
  for(var i=0;i<state.tasks.length;i++){
    var t=state.tasks[i];
    if(t.done){
      doneCount++;
      if(t.completedAt){
        var c=fmtDate(new Date(t.completedAt));
        if(c===today) todayDone++;
        if(c>=wr.mon && c<=wr.sun) weekDone++;
      }
    }else{
      pending++;
      if(t.due && t.due<today) overdue++;
    }
  }
  qs('#cntTodo').textContent=pending;
  qs('#cntDone').textContent=doneCount;
  qs('#stats').innerHTML=
    '<span class="chip">待办 <b>'+pending+'</b></span>'+
    '<span class="chip'+(overdue>0?' overdue':'')+'">已过期 <b>'+overdue+'</b></span>'+
    '<span class="chip">今日完成 <b>'+todayDone+'</b></span>'+
    '<span class="chip">本周完成 <b>'+weekDone+'</b></span>';
}
function renderToolbar(){
  var todoTab = ui.tab==='todo';
  qs('#filterGroup').style.display = todoTab?'contents':'none';
  qs('#btnClearDone').hidden = todoTab;
  qs('#selFilter').value=ui.filter;
  qs('#selSort').value=ui.sort;
  qs('#search').value=ui.q;
  if(!state.categories.some(function(c){ return c.id===ui.cat; })) ui.cat='';
  fillCatSelect(qs('#qaCat'),'无分类');
}
function taskRow(t){
  var li=document.createElement('li');
  li.className='task'+(t.done?' done':'');
  li.setAttribute('data-id',t.id);

  var cb=document.createElement('button');
  cb.className='check';
  cb.title=t.done?'恢复为待办':'标记完成';
  cb.textContent=t.done?'✓':'';
  cb.addEventListener('click',function(e){
    e.stopPropagation();
    if(t.done) restoreTask(t.id); else completeTask(t.id);
  });

  var body=document.createElement('div');
  body.className='task-body';

  var titleRow=document.createElement('div');
  titleRow.className='task-title';
  var span=document.createElement('span');
  span.className='t-text';
  span.textContent=t.title;
  titleRow.appendChild(span);
  body.appendChild(titleRow);

  if(t.note){
    var np=document.createElement('div');
    np.className='note-prev';
    np.textContent=t.note;
    body.appendChild(np);
  }

  var meta=document.createElement('div');
  meta.className='task-meta';
  if(t.due){
    var di=dueInfo(t.due);
    var bd=document.createElement('span');
    bd.className='badge due '+di.cls;
    bd.textContent='📅 '+di.label;
    meta.appendChild(bd);
  }
  if(t.priority && t.priority!=='none' && PRIO[t.priority]){
    var bp=document.createElement('span');
    bp.className='badge prio '+PRIO[t.priority].cls;
    bp.textContent=PRIO[t.priority].label+'优先级';
    meta.appendChild(bp);
  }
  if(t.repeat && t.repeat!=='none' && REPEAT[t.repeat]){
    var br=document.createElement('span');
    br.className='badge rep';
    br.textContent='🔁 '+REPEAT[t.repeat].label;
    meta.appendChild(br);
  }
  if(t.subtasks && t.subtasks.length){
    var sc=0;
    for(var si=0;si<t.subtasks.length;si++){ if(t.subtasks[si].done) sc++; }
    var bs=document.createElement('span');
    bs.className='badge sub';
    bs.textContent='子任务 '+sc+'/'+t.subtasks.length;
    meta.appendChild(bs);
  }
  if(t.categoryId){
    var cat=findCat(t.categoryId);
    if(cat){
      var bc=document.createElement('span');
      bc.className='badge cat';
      var dot=document.createElement('span');
      dot.className='dot';
      dot.style.background=cat.color;
      bc.appendChild(dot);
      bc.appendChild(document.createTextNode(cat.name));
      bc.title='只看这个分类';
      bc.addEventListener('click',function(e){
        e.stopPropagation();
        ui.cat=cat.id; ui.tab='todo';
        render();
      });
      meta.appendChild(bc);
    }
  }
  if(t.done && t.completedAt){
    var d=new Date(t.completedAt);
    var bf=document.createElement('span');
    bf.className='badge doneat';
    bf.textContent='完成于 '+(d.getMonth()+1)+'月'+d.getDate()+'日 '+pad(d.getHours())+':'+pad(d.getMinutes());
    meta.appendChild(bf);
  }
  body.appendChild(meta);

  if(t.subtasks && t.subtasks.length) renderSubs(body, t);
  if(!t.done){
    var subAdd=document.createElement('div');
    subAdd.className='sub-add';
    var sab=document.createElement('button');
    sab.className='sub-add-btn';
    sab.textContent='＋ 子任务';
    sab.title='添加子任务';
    sab.addEventListener('click',function(e){
      e.stopPropagation();
      startSubtaskAdd(t, subAdd);
    });
    subAdd.appendChild(sab);
    body.appendChild(subAdd);
  }

  var actions=document.createElement('div');
  actions.className='task-actions';
  if(!t.done){
    var eb=document.createElement('button');
    eb.className='icon-btn';
    eb.textContent='✎';
    eb.title='编辑';
    eb.addEventListener('click',function(e){ e.stopPropagation(); startEdit(t); });
    actions.appendChild(eb);
  }
  var db=document.createElement('button');
  db.className='icon-btn';
  db.textContent='🗑';
  db.title='删除';
  db.addEventListener('click',function(e){ e.stopPropagation(); removeTask(t.id); });
  actions.appendChild(db);

  li.appendChild(cb);
  li.appendChild(body);
  li.appendChild(actions);
  if(!t.done){
    li.addEventListener('click',function(){ startEdit(t); });
  }
  return li;
}
function renderSubs(container, t){
  var ul=document.createElement('ul');
  ul.className='subtasks';
  for(var i=0;i<t.subtasks.length;i++){
    (function(st){
      var li=document.createElement('li');
      li.className='sub-row'+(st.done?' done':'');
      var cb=document.createElement('button');
      cb.className='sub-check';
      cb.title=st.done?'标记未完成':'标记完成';
      cb.textContent=st.done?'✓':'';
      cb.addEventListener('click',function(e){
        e.stopPropagation();
        st.done=!st.done;
        st.completedAt=st.done?Date.now():null;
        t.updatedAt=Date.now();
        saveState(); render();
      });
      var sp=document.createElement('span');
      sp.className='sub-text';
      sp.textContent=st.title;
      var del=document.createElement('button');
      del.className='icon-btn sub-del';
      del.textContent='✕';
      del.title='删除子任务';
      del.addEventListener('click',function(e){
        e.stopPropagation();
        t.subtasks=t.subtasks.filter(function(x){ return x.id!==st.id; });
        t.updatedAt=Date.now();
        saveState(); render();
      });
      li.appendChild(cb);
      li.appendChild(sp);
      li.appendChild(del);
      ul.appendChild(li);
    })(t.subtasks[i]);
  }
  container.appendChild(ul);
}
function startSubtaskAdd(t, addRow){
  var input=document.createElement('input');
  input.type='text';
  input.maxLength=200;
  input.placeholder='子任务内容，回车保存';
  var finished=false;
  function commit(){
    if(finished) return;
    finished=true;
    var v=input.value.trim();
    if(v){
      t.subtasks=t.subtasks||[];
      t.subtasks.push({id:uid(),title:v,done:false,createdAt:Date.now(),completedAt:null});
      t.updatedAt=Date.now();
      saveState(); render();
    }else{
      render();
    }
  }
  input.addEventListener('keydown',function(e){
    if(e.key==='Enter'){ e.preventDefault(); commit(); }
    else if(e.key==='Escape'){ input.blur(); }
  });
  input.addEventListener('blur',commit);
  addRow.innerHTML='';
  addRow.appendChild(input);
  input.focus();
}
function renderList(){
  var list=qs('#taskList');
  list.innerHTML='';
  var tasks=state.tasks.filter(function(t){ return ui.tab==='done'?t.done:!t.done; });
  if(ui.tab==='done'){
    tasks.sort(function(a,b){ return (b.completedAt||0)-(a.completedAt||0); });
  }else{
    tasks=tasks.filter(matchFilter);
    var fn = ui.sort==='due'?cmpDue : ui.sort==='priority'?cmpPrio : ui.sort==='created'?cmpCreated : cmpSmart;
    tasks.sort(fn);
  }
  var empty=qs('#emptyState');
  if(tasks.length===0){
    empty.hidden=false;
    if(ui.tab==='done'){
      empty.innerHTML='<div>还没有完成的任务。</div><div class="sub">在「待办」里点圆圈 ✓ 完成任务后会出现在这里。</div>';
    }else{
      var totalPending=state.tasks.filter(function(t){ return !t.done; }).length;
      if(totalPending===0){
        empty.innerHTML='<div>🎉 没有待办任务</div><div class="sub">在上方输入框写下第一件事，回车即可添加。</div>';
      }else{
        empty.innerHTML='<div>没有符合条件的任务。</div><div class="sub">试试调整筛选条件或搜索关键词。</div>';
      }
    }
  }else{
    empty.hidden=true;
    for(var i=0;i<tasks.length;i++) list.appendChild(taskRow(tasks[i]));
  }
}
function renderCatManager(){
  var ul=qs('#catList');
  ul.innerHTML='';
  for(var i=0;i<state.categories.length;i++){
    (function(c){
      var li=document.createElement('li');
      li.className='cat-row';
      var dot=document.createElement('span');
      dot.className='cat-dot';
      dot.style.background=c.color;
      dot.title='点击更换颜色';
      dot.addEventListener('click',function(){
        var idx=PALETTE.indexOf(c.color);
        c.color=PALETTE[(idx+1)%PALETTE.length];
        c.updatedAt=Date.now();
        saveState(); render();
      });
      var inp=document.createElement('input');
      inp.type='text';
      inp.value=c.name;
      inp.maxLength=20;
      inp.addEventListener('change',function(){
        var v=inp.value.trim();
        if(v && v!==c.name){ c.name=v; c.updatedAt=Date.now(); saveState(); render(); }
        else if(!v){ inp.value=c.name; }
      });
      var del=document.createElement('button');
      del.className='icon-btn';
      del.textContent='🗑';
      del.title='删除分类';
      del.addEventListener('click',function(){
        if(!confirm('删除分类「'+c.name+'」？该分类下的任务会变为无分类，任务本身保留。')) return;
        state.tasks.forEach(function(t){ if(t.categoryId===c.id) t.categoryId=null; });
        state.categories=state.categories.filter(function(x){ return x.id!==c.id; });
        addTombstone('c:'+c.id);
        if(ui.cat===c.id) ui.cat='';
        saveState(); render();
      });
      li.appendChild(dot);
      li.appendChild(inp);
      li.appendChild(del);
      ul.appendChild(li);
    })(state.categories[i]);
  }
}
function notifyStatusText(){
  if(!('Notification' in window)) return '当前浏览器不支持通知。';
  var p=Notification.permission;
  if(p==='granted') return '浏览器通知权限：已允许 ✅';
  if(p==='denied') return '浏览器通知权限：已被拒绝 ❌（需在浏览器设置里手动允许本站通知）';
  return '浏览器通知权限：未授权，点上方按钮开启。';
}
function renderSettingsForm(){
  qs('#setTheme').value=state.settings.theme||'system';
  qs('#setNotify').checked=!!state.settings.notify;
  qs('#setAdvance').value=String(state.settings.advance||'0');
  qs('#notifyStatus').textContent=notifyStatusText();
}
function renderSyncUI(){
  var banner=qs('#syncBanner');
  var shouldShow = !fileHandle && localStorage.getItem(LS_SYNC)==='1' && (typeof window.showOpenFilePicker==='function' || typeof window.showSaveFilePicker==='function');
  banner.hidden=!shouldShow;
}
function catItem(o){
  var li=document.createElement('li');
  var b=document.createElement('button');
  b.className='side-cat'+(o.active?' active':'');
  var dot=document.createElement('span');
  dot.className='dot';
  if(o.color){ dot.style.background=o.color; }
  else{ dot.style.border='1px dashed var(--border)'; }
  b.appendChild(dot);
  var name=document.createElement('span');
  name.className='name';
  name.textContent=o.name;
  b.appendChild(name);
  var cnt=document.createElement('span');
  cnt.className='count';
  cnt.textContent=o.count;
  b.appendChild(cnt);
  b.title=o.id?('只看「'+o.name+'」（再点一次取消筛选）'):'查看全部';
  b.addEventListener('click',function(){
    ui.cat=(ui.cat===o.id)?'':o.id;
    ui.tab='todo';
    render();
  });
  li.appendChild(b);
  return li;
}
function renderSidebar(){
  var todoTab = ui.tab==='todo';
  qs('#tabTodo').classList.toggle('active', todoTab);
  qs('#tabDone').classList.toggle('active', !todoTab);
  var ul=qs('#sideCatList');
  ul.innerHTML='';
  var pendingTotal=0;
  var perCat={};
  for(var i=0;i<state.tasks.length;i++){
    var t=state.tasks[i];
    if(t.done) continue;
    pendingTotal++;
    if(t.categoryId) perCat[t.categoryId]=(perCat[t.categoryId]||0)+1;
  }
  ul.appendChild(catItem({id:'', name:'全部', color:null, count:pendingTotal, active:ui.cat===''}));
  for(var j=0;j<state.categories.length;j++){
    var c=state.categories[j];
    ul.appendChild(catItem({id:c.id, name:c.name, color:c.color, count:perCat[c.id]||0, active:ui.cat===c.id}));
  }
  if(state.categories.length===0){
    var li=document.createElement('li');
    li.className='side-hint';
    li.textContent='还没有分类，点「＋」添加';
    ul.appendChild(li);
  }
}
function render(){
  applyTheme();
  renderHeader();
  renderSidebar();
  renderStats();
  renderToolbar();
  renderList();
  renderCatManager();
  renderSettingsForm();
  renderSyncUI();
}

/* ================= 快速添加 / 编辑 ================= */
function resetAddForm(){
  qs('#qaTitle').value='';
  qs('#qaDue').value='';
  qs('#qaPrio').value='none';
  qs('#qaRepeat').value='none';
  qs('#qaNote').value='';
  fillCatSelect(qs('#qaCat'),'无分类');
}
function exitEditMode(){
  editingId=null;
  qs('#btnSubmit').textContent='添加';
  qs('#btnCancelEdit').hidden=true;
  qs('#qaExtra').hidden=true;
}
function submitAdd(){
  var title=qs('#qaTitle').value.trim();
  if(!title){ toast('先输入任务内容'); return; }
  var wasEditing=!!editingId;
  if(editingId){
    for(var i=0;i<state.tasks.length;i++){
      if(state.tasks[i].id===editingId){
        var t=state.tasks[i];
        t.title=title;
        t.due=qs('#qaDue').value||null;
        t.priority=qs('#qaPrio').value;
        t.categoryId=qs('#qaCat').value||null;
        t.repeat=qs('#qaRepeat').value;
        t.note=qs('#qaNote').value.trim();
        t.updatedAt=Date.now();
        break;
      }
    }
  }else{
    state.tasks.push({
      id:uid(),
      title:title,
      note:qs('#qaNote').value.trim(),
      due:qs('#qaDue').value||null,
      priority:qs('#qaPrio').value,
      categoryId:qs('#qaCat').value||null,
      repeat:qs('#qaRepeat').value,
      done:false, createdAt:Date.now(), completedAt:null, updatedAt:Date.now(), subtasks:[]
    });
  }
  resetAddForm();
  exitEditMode();
  saveState(); render();
  toast(wasEditing?'已保存':'已添加');
}
function startEdit(t){
  editingId=t.id;
  qs('#qaTitle').value=t.title;
  qs('#qaDue').value=t.due||'';
  qs('#qaPrio').value=t.priority||'none';
  qs('#qaRepeat').value=t.repeat||'none';
  qs('#qaNote').value=t.note||'';
  fillCatSelect(qs('#qaCat'),'无分类');
  qs('#qaCat').value=t.categoryId||'';
  qs('#btnSubmit').textContent='保存';
  qs('#btnCancelEdit').hidden=false;
  qs('#qaExtra').hidden=false;
  qs('#qaTitle').focus();
  window.scrollTo({top:0,behavior:'smooth'});
}

/* ================= 弹窗与提示 ================= */
var toastTimer=null;
function toast(msg){
  var t=qs('#toast');
  t.textContent=msg;
  t.hidden=false;
  if(toastTimer) clearTimeout(toastTimer);
  toastTimer=setTimeout(function(){ t.hidden=true; },2600);
}
function openModal(id){ qs(id).hidden=false; }

/* ================= 数据文件同步（File System Access API） ================= */
function supportsPicker(){
  return typeof window.showSaveFilePicker==='function' || typeof window.showOpenFilePicker==='function';
}
var conflictResolver=null;
function askConflict(){
  return new Promise(function(res){
    conflictResolver=res;
    qs('#modalConflict').hidden=false;
  });
}
function resolveConflict(v){
  if(conflictResolver){ var r=conflictResolver; conflictResolver=null; r(v); }
}
async function ensurePerm(h){
  try{
    var p=await h.queryPermission({mode:'readwrite'});
    if(p!=='granted') p=await h.requestPermission({mode:'readwrite'});
    return p==='granted';
  }catch(e){ return false; }
}
async function writeFileNow(){
  if(!fileHandle) return;
  try{
    var w=await fileHandle.createWritable();
    await w.write(JSON.stringify(state,null,2));
    await w.close();
  }catch(err){
    console.error('同步失败',err);
    toast('同步到数据文件失败：'+err.message);
  }
}
async function connectFile(){
  if(!supportsPicker()){
    toast('当前浏览器不支持数据文件同步（需要 Chrome 或 Edge）。可改用「📤 导出」手动备份。');
    return;
  }
  try{
    var handle;
    var hadSync=localStorage.getItem(LS_SYNC)==='1';
    if(hadSync && typeof window.showOpenFilePicker==='function'){
      var picked=await window.showOpenFilePicker({
        multiple:false,
        types:[{description:'工作台数据文件',accept:{'application/json':['.json']}}]
      });
      handle=picked[0];
      var f=await handle.getFile();
      var text=await f.text();
      var fileState=null;
      try{ fileState=JSON.parse(text); }catch(e){}
      var fileOk = fileState && Array.isArray(fileState.tasks);
      var localHas = state.tasks.length>0 || state.categories.length>0;
      var fileHas = fileOk && (fileState.tasks.length>0 || (Array.isArray(fileState.categories)&&fileState.categories.length>0));
      if(fileHas && localHas){
        var choice=await askConflict();
        if(choice==='cancel') return;
        if(choice==='file'){ state=normalize(fileState); saveState(); render(); }
      }else if(fileHas && !localHas){
        state=normalize(fileState); saveState(); render();
      }else if(!fileOk && text && text.trim()){
        toast('所选文件内容无法识别，将用浏览器数据覆盖。');
      }
    }else{
      handle=await window.showSaveFilePicker({
        suggestedName:'workbench-data.json',
        types:[{description:'工作台数据文件',accept:{'application/json':['.json']}}]
      });
    }
    fileHandle=handle;
    await ensurePerm(handle);
    await writeFileNow();
    localStorage.setItem(LS_SYNC,'1');
    renderSyncUI();
    toast('已连接数据文件，之后每次修改都会自动同步保存。');
  }catch(err){
    if(err && err.name!=='AbortError'){
      console.error(err);
      toast('连接数据文件失败：'+(err.message||err));
    }
  }
}

/* ================= 云同步（GitHub 仓库 + 密码加密） ================= */
function bytesToB64(bytes){
  var bin='';
  for(var i=0;i<bytes.length;i++){ bin+=String.fromCharCode(bytes[i]); }
  return btoa(bin);
}
function b64ToBytes(b64){
  var bin=atob(b64);
  var out=new Uint8Array(bin.length);
  for(var i=0;i<bin.length;i++){ out[i]=bin.charCodeAt(i); }
  return out;
}
function utf8B64(s){ return bytesToB64(new TextEncoder().encode(s)); }
function b64Utf8(b){ return new TextDecoder().decode(b64ToBytes(b)); }
function b64urlEncode(s){ return utf8B64(s).replace(/\+/g,'-').replace(/\//g,'_').replace(/=+$/,''); }
function b64urlDecode(s){
  var b=s.replace(/-/g,'+').replace(/_/g,'/');
  while(b.length%4) b+='=';
  return b64Utf8(b);
}
async function deriveKey(password, salt){
  var enc=new TextEncoder();
  var base=await crypto.subtle.importKey('raw', enc.encode(password), 'PBKDF2', false, ['deriveKey']);
  return await crypto.subtle.deriveKey(
    {name:'PBKDF2', salt:salt, iterations:150000, hash:'SHA-256'},
    base, {name:'AES-GCM', length:256}, false, ['encrypt','decrypt']
  );
}
async function encryptPayload(obj, password){
  var salt=crypto.getRandomValues(new Uint8Array(16));
  var iv=crypto.getRandomValues(new Uint8Array(12));
  var key=await deriveKey(password, salt);
  var ct=await crypto.subtle.encrypt({name:'AES-GCM', iv:iv}, key, new TextEncoder().encode(JSON.stringify(obj)));
  return {v:1, kdf:'pbkdf2-sha256', iter:150000, salt:bytesToB64(salt), iv:bytesToB64(iv), ct:bytesToB64(new Uint8Array(ct))};
}
async function decryptPayload(wrap, password){
  var salt=b64ToBytes(wrap.salt);
  var iv=b64ToBytes(wrap.iv);
  var ct=b64ToBytes(wrap.ct);
  var key=await deriveKey(password, salt);
  var pt=await crypto.subtle.decrypt({name:'AES-GCM', iv:iv}, key, ct);
  return JSON.parse(new TextDecoder().decode(pt));
}
function ghUrl(cfg){
  return 'https://api.github.com/repos/'+encodeURIComponent(cfg.owner)+'/'+encodeURIComponent(cfg.repo)+'/contents/'+encodeURIComponent(cfg.path||'workbench-data.json');
}
function ghHeaders(cfg){
  return { Authorization:'Bearer '+cfg.token, Accept:'application/vnd.github+json' };
}
async function ghGet(cfg){
  var u=ghUrl(cfg)+(cfg.branch?('?ref='+encodeURIComponent(cfg.branch)):'');
  var res=await fetch(u,{headers:ghHeaders(cfg)});
  if(res.status===404) return null;
  if(!res.ok){ var e=new Error('GitHub 读取失败 '+res.status); e.status=res.status; throw e; }
  return await res.json();
}
async function ghPut(cfg, b64, sha){
  var body={message:'workbench data update', content:b64};
  if(sha) body.sha=sha;
  if(cfg.branch) body.branch=cfg.branch;
  var res=await fetch(ghUrl(cfg),{method:'PUT',headers:ghHeaders(cfg),body:JSON.stringify(body)});
  if(!res.ok){ var e=new Error('GitHub 保存失败 '+res.status); e.status=res.status; throw e; }
  return await res.json();
}
function mergeStates(local, remote, lastSync){
  function better(l, r, ls){
    var lm=l.updatedAt>ls, rm=r.updatedAt>ls;
    if(lm && rm) return r;
    if(rm) return r;
    if(lm) return l;
    return (r.updatedAt>=l.updatedAt)?r:l;
  }
  function mergeArr(localArr, remoteArr, prefix, ls){
    var map={};
    localArr.forEach(function(x){ map[x.id]=x; });
    var out=[];
    remoteArr.forEach(function(r){
      var l=map[r.id];
      if(tombstones[prefix+r.id] && tombstones[prefix+r.id]>ls) return;
      if(l){ out.push(better(l,r,ls)); delete map[r.id]; }
      else{ out.push(r); }
    });
    localArr.forEach(function(x){
      if(!(x.id in map)) return;
      if(x.updatedAt>ls) out.push(x);
    });
    return out;
  }
  return {
    tasks:mergeArr(local.tasks, remote.tasks, 't:', lastSync),
    categories:mergeArr(local.categories, remote.categories, 'c:', lastSync)
  };
}
function loadCloudConfig(){
  var cfg=null;
  try{
    var m=(location.hash||'').match(/[#&]c=([A-Za-z0-9_-]+)/);
    if(m){
      var j=JSON.parse(b64urlDecode(m[1]));
      if(j && j.owner && j.repo && j.token){
        cfg={owner:String(j.owner),repo:String(j.repo),branch:String(j.branch||''),path:String(j.path||'workbench-data.json'),token:String(j.token)};
      }
    }
  }catch(e){}
  if(!cfg){
    try{
      var s=localStorage.getItem(LS_CLOUD);
      if(s){
        var c=JSON.parse(s);
        if(c && c.owner && c.repo && c.token) cfg=c;
      }
    }catch(e){}
  }
  return cfg;
}
function saveCloudConfig(cfg){
  try{ localStorage.setItem(LS_CLOUD, JSON.stringify(cfg)); }catch(e){}
}
function clearCloudConfig(){
  try{ localStorage.removeItem(LS_CLOUD); localStorage.removeItem(LS_CLOUD_PW); }catch(e){}
}
function setSyncStatus(kind, msg){
  var b=qs('#syncBadge');
  if(kind==='off'){ b.hidden=true; return; }
  b.hidden=false;
  b.className='sync-badge'+(kind==='error'?' err':'');
  if(kind==='ok') b.textContent='☁️ 已同步';
  else if(kind==='pending') b.textContent='☁️ 同步中…';
  else if(kind==='offline') b.textContent='☁️ 离线';
  else b.textContent='☁️ 同步失败';
  b.title=msg||'';
}
function showLock(autoMsg){
  qs('#lockScreen').hidden=false;
  qs('#lockError').hidden=true;
  qs('#lockPw').value='';
  if(autoMsg){ qs('#lockPw').placeholder=autoMsg; }
  setSyncStatus('offline','等待解锁');
  if(qs('#cloudStatus')) qs('#cloudStatus').textContent='已配置（等待解锁）';
}
function hideLock(){ qs('#lockScreen').hidden=true; }
function showLockError(msg){
  var el=qs('#lockError');
  el.textContent=msg;
  el.hidden=false;
}
function offlineOpen(){
  cloud.enabled=false;
  cloud.key=null;
  hideLock();
  setSyncStatus('offline','当前离线，改动只存在本机，联网并解锁后自动同步');
  toast('已进入离线模式（使用本地数据）');
}
async function unlock(password, remember){
  if(!window.crypto || !crypto.subtle){
    showLockError('当前环境不支持数据加密（请用 HTTPS 链接或本机文件打开）');
    return;
  }
  try{
    var file=await ghGet(cloud.cfg);
    var sha;
    if(file){
      var wrap=JSON.parse(b64Utf8(file.content.replace(/\s+/g,'')));
      var payload=await decryptPayload(wrap, password);
      sha=file.sha;
      var merged=mergeStates(state, payload, 0);
      state.tasks=merged.tasks;
      state.categories=merged.categories;
    }else{
      var w=await encryptPayload({v:1, tasks:state.tasks, categories:state.categories}, password);
      var res=await ghPut(cloud.cfg, utf8B64(JSON.stringify(w)), null);
      sha=res.content.sha;
    }
    cloud.key=password;
    cloud.enabled=true;
    cloud.lastSha=sha;
    cloud.lastSync=0;
    if(remember){ try{ localStorage.setItem(LS_CLOUD_PW, password); }catch(e){} }
    hideLock();
    saveLocal();
    render();
    if(qs('#cloudStatus')) qs('#cloudStatus').textContent='已连接';
    startPolling();
    schedulePush(400);
    setSyncStatus('pending');
    toast(file?'已解锁，开始同步':'已创建共享数据');
  }catch(err){
    if(err && err.name==='OperationError'){ showLockError('密码错误，请重试'); }
    else{ showLockError('连接失败：'+(err.message||err)+'（请检查网络、仓库名和 Token）'); }
  }
}
function pruneTombstones(){
  var keys=Object.keys(tombstones), changed=false;
  for(var i=0;i<keys.length;i++){
    var k=keys[i];
    var arr = k.charAt(0)==='t'?state.tasks:state.categories;
    var id=k.slice(2), exists=false;
    for(var j=0;j<arr.length;j++){ if(arr[j].id===id){ exists=true; break; } }
    if(!exists && tombstones[k]<=cloud.lastSync){ delete tombstones[k]; changed=true; }
  }
  if(changed) saveTombstones();
}
async function pushCycle(){
  if(!cloud.enabled || cloud.pushing) return;
  cloud.pushing=true;
  var seqStart=cloud.dirtySeq;
  try{
    for(var attempt=0; attempt<3; attempt++){
      var file=await ghGet(cloud.cfg);
      var sha=file?file.sha:null;
      var snapTime=Date.now();
      var payload=null;
      if(file){
        var wrap=JSON.parse(b64Utf8(file.content.replace(/\s+/g,'')));
        payload=await decryptPayload(wrap, cloud.key);
      }else{
        payload={v:1, tasks:[], categories:[]};
      }
      var merged=mergeStates(state, payload, cloud.lastSync);
      var mergedJson=JSON.stringify({tasks:merged.tasks, categories:merged.categories});
      var remoteJson=JSON.stringify({tasks:payload.tasks, categories:payload.categories});
      if(mergedJson===remoteJson){
        cloud.lastSha=sha;
        cloud.lastSync=snapTime;
        if(cloud.dirtySeq===seqStart) cloud.dirty=false;
        setSyncStatus('ok');
        break;
      }
      state.tasks=merged.tasks;
      state.categories=merged.categories;
      var w=await encryptPayload({v:1, tasks:merged.tasks, categories:merged.categories}, cloud.key);
      var res;
      try{
        res=await ghPut(cloud.cfg, utf8B64(JSON.stringify(w)), sha);
      }catch(e2){
        if(e2.status===409 || e2.status===422){ continue; }
        throw e2;
      }
      cloud.lastSha=res.content.sha;
      cloud.lastSync=snapTime;
      if(cloud.dirtySeq===seqStart) cloud.dirty=false;
      saveLocal();
      render();
      pruneTombstones();
      setSyncStatus('ok');
      break;
    }
  }catch(err){
    if(!navigator.onLine){ setSyncStatus('offline', '网络不可用，改动会在联网后自动同步'); }
    else{ setSyncStatus('error', err.message||String(err)); }
  }
  cloud.pushing=false;
  if(cloud.dirty && cloud.dirtySeq!==seqStart) schedulePush(300);
}
function schedulePush(ms){
  if(!cloud.enabled) return;
  if(cloud.pushTimer) clearTimeout(cloud.pushTimer);
  cloud.pushTimer=setTimeout(pushCycle, ms||900);
}
async function pollOnce(){
  if(!cloud.enabled || cloud.pushing) return;
  try{
    var file=await ghGet(cloud.cfg);
    if(!file) return;
    if(file.sha===cloud.lastSha){ if(navigator.onLine) setSyncStatus('ok'); return; }
    var snapTime=Date.now();
    var wrap=JSON.parse(b64Utf8(file.content.replace(/\s+/g,'')));
    var payload=await decryptPayload(wrap, cloud.key);
    var merged=mergeStates(state, payload, cloud.lastSync);
    state.tasks=merged.tasks;
    state.categories=merged.categories;
    cloud.lastSha=file.sha;
    cloud.lastSync=snapTime;
    saveLocal();
    render();
    setSyncStatus('ok');
    if(cloud.dirty) schedulePush(100);
  }catch(err){
    if(!navigator.onLine){ setSyncStatus('offline', '网络不可用，改动会在联网后自动同步'); }
    else{ setSyncStatus('error', err.message||String(err)); }
  }
}
function startPolling(){
  stopPolling();
  cloud.pollTimer=setInterval(pollOnce, 5000);
}
function stopPolling(){
  if(cloud.pollTimer){ clearInterval(cloud.pollTimer); cloud.pollTimer=null; }
  if(cloud.pushTimer){ clearTimeout(cloud.pushTimer); cloud.pushTimer=null; }
}
function renderCloudUI(){
  var has=!!cloud.cfg;
  var st=qs('#cloudStatus');
  if(st) st.textContent = has ? (cloud.enabled?'已连接':'已配置（未解锁）') : '未配置';
  if(has){
    qs('#cfgOwner').value=cloud.cfg.owner||'';
    qs('#cfgRepo').value=cloud.cfg.repo||'';
    qs('#cfgBranch').value=cloud.cfg.branch||'';
    qs('#cfgPath').value=cloud.cfg.path||'workbench-data.json';
    qs('#cfgToken').value=cloud.cfg.token||'';
    qs('#cfgPages').value=cloud.cfg.pages||'';
  }
  qs('#btnCloudNow').hidden=!cloud.enabled;
  qs('#btnCloudOff').hidden=!has;
}

/* ================= 导出 / 导入 ================= */
function exportData(){
  var blob=new Blob([JSON.stringify(state,null,2)],{type:'application/json'});
  var url=URL.createObjectURL(blob);
  var a=document.createElement('a');
  a.href=url;
  a.download='workbench-backup-'+todayStr()+'.json';
  document.body.appendChild(a);
  a.click();
  a.remove();
  setTimeout(function(){ URL.revokeObjectURL(url); },1000);
  toast('已导出备份文件（下载目录）');
}
function importFile(file){
  var reader=new FileReader();
  reader.onload=function(){
    try{
      var data=JSON.parse(reader.result);
      if(!data || !Array.isArray(data.tasks)){ toast('文件格式不对：缺少任务数据'); return; }
      if(!confirm('导入将覆盖当前全部数据（任务、分类、设置）。确定继续？')) return;
      state=normalize(data);
      saveState(); render();
      toast('导入成功');
    }catch(e){ toast('导入失败：'+e.message); }
  };
  reader.readAsText(file);
}

/* ================= 事件绑定 ================= */
function bindEvents(){
  qs('#btnSubmit').addEventListener('click',submitAdd);
  qs('#qaTitle').addEventListener('keydown',function(e){
    if(e.key==='Enter'){ e.preventDefault(); submitAdd(); }
  });
  qs('#btnMore').addEventListener('click',function(){
    var extra=qs('#qaExtra');
    extra.hidden=!extra.hidden;
  });
  qs('#btnCancelEdit').addEventListener('click',function(){
    resetAddForm(); exitEditMode();
  });
  qs('#tabTodo').addEventListener('click',function(){ ui.tab='todo'; render(); });
  qs('#tabDone').addEventListener('click',function(){ ui.tab='done'; render(); });
  qs('#search').addEventListener('input',function(){ ui.q=qs('#search').value; renderList(); });
  qs('#selFilter').addEventListener('change',function(){ ui.filter=qs('#selFilter').value; renderList(); });
  qs('#selSort').addEventListener('change',function(){ ui.sort=qs('#selSort').value; renderList(); });
  qs('#btnClearDone').addEventListener('click',clearDone);

  qs('#btnTheme').addEventListener('click',function(){
    var order=['system','light','dark'];
    var cur=order.indexOf(state.settings.theme)>=0?state.settings.theme:'system';
    var next=order[(order.indexOf(cur)+1)%order.length];
    state.settings.theme=next;
    saveState(); render();
    qs('#btnTheme').textContent=THEME_ICON[next];
    toast('主题：'+THEME_LABEL[next]);
  });

  qs('#btnSettings').addEventListener('click',function(){ renderSettingsForm(); openModal('#modalSettings'); });
  qs('#btnCats').addEventListener('click',function(){ openModal('#modalCats'); });
  qs('#btnAddCatQuick').addEventListener('click',function(){
    openModal('#modalCats');
    qs('#newCatName').focus();
  });
  qs('#btnAddCat').addEventListener('click',addCat);
  qs('#newCatName').addEventListener('keydown',function(e){
    if(e.key==='Enter'){ e.preventDefault(); addCat(); }
  });
  function addCat(){
    var name=qs('#newCatName').value.trim();
    if(!name){ toast('请输入分类名称'); return; }
    if(state.categories.some(function(c){ return c.name===name; })){ toast('已有同名分类'); return; }
    state.categories.push({id:uid(),name:name,color:nextCatColor(),updatedAt:Date.now()});
    qs('#newCatName').value='';
    saveState(); render();
  }

  qs('#setTheme').addEventListener('change',function(){
    state.settings.theme=qs('#setTheme').value;
    saveState(); render();
  });
  qs('#setNotify').addEventListener('change',function(){
    state.settings.notify=qs('#setNotify').checked;
    saveState();
    if(state.settings.notify && 'Notification' in window && Notification.permission==='default'){
      Notification.requestPermission().then(function(){ renderSettingsForm(); }).catch(function(){});
    }
  });
  qs('#setAdvance').addEventListener('change',function(){
    state.settings.advance=qs('#setAdvance').value;
    saveState();
  });
  qs('#btnNotifyPerm').addEventListener('click',async function(){
    if(!('Notification' in window)){ toast('当前浏览器不支持通知'); return; }
    try{
      var p=await Notification.requestPermission();
      toast(p==='granted'?'通知权限已开启':(p==='denied'?'通知被拒绝，请在浏览器设置中手动允许':'未授权'));
    }catch(e){ toast('请求通知权限失败：'+e.message); }
    renderSettingsForm();
  });
  qs('#btnClearAll').addEventListener('click',function(){
    if(!confirm('确定清空全部数据？任务、分类、设置都会被删除，且无法恢复。建议先点「📤 导出」备份。')) return;
    state.tasks.forEach(function(t){ addTombstone('t:'+t.id); });
    state.categories.forEach(function(c){ addTombstone('c:'+c.id); });
    state=defaultState();
    saveState(); render();
    toast('已清空');
  });

  qs('#btnSaveCloud').addEventListener('click',function(){
    var owner=qs('#cfgOwner').value.trim();
    var repo=qs('#cfgRepo').value.trim();
    var token=qs('#cfgToken').value.trim();
    if(!owner||!repo||!token){ toast('请填写用户名、仓库名和 Token'); return; }
    var cfg={
      owner:owner, repo:repo,
      branch:qs('#cfgBranch').value.trim(),
      path:qs('#cfgPath').value.trim()||'workbench-data.json',
      token:token,
      pages:qs('#cfgPages').value.trim()
    };
    saveCloudConfig(cfg);
    cloud.cfg=cfg;
    stopPolling();
    cloud.enabled=false; cloud.key=null;
    renderCloudUI();
    showLock();
    toast('配置已保存，请输入访问密码');
  });
  qs('#btnShareLink').addEventListener('click',function(){
    var cfg=cloud.cfg;
    if(!cfg){ toast('请先保存云同步配置'); return; }
    var frag=b64urlEncode(JSON.stringify({owner:cfg.owner,repo:cfg.repo,branch:cfg.branch,path:cfg.path,token:cfg.token}));
    var prefix=(qs('#cfgPages').value||cfg.pages||'').trim().replace(/\/+$/,'');
    var link=(prefix?prefix+'/':'（你的 GitHub Pages 地址，如 https://用户名.github.io/仓库名/ ）')+'#'+'c='+frag;
    var out=qs('#shareLinkOut');
    out.hidden=false;
    out.value=link;
    if(navigator.clipboard && navigator.clipboard.writeText){
      navigator.clipboard.writeText(link).then(function(){ toast('共享链接已复制到剪贴板'); }, function(){ out.select(); toast('链接已生成，请手动复制'); });
    }else{
      out.select();
      toast('链接已生成，请手动复制');
    }
  });
  qs('#btnCloudNow').addEventListener('click',function(){ setSyncStatus('pending'); pushCycle(); });
  qs('#btnCloudOff').addEventListener('click',function(){
    if(!confirm('断开云同步？本地数据保留，之后不再自动同步。')) return;
    stopPolling();
    cloud.enabled=false; cloud.key=null; cloud.cfg=null; cloud.lastSha=null;
    clearCloudConfig();
    setSyncStatus('off');
    renderCloudUI();
    toast('已断开云同步（本地数据保留）');
  });
  qs('#btnUnlock').addEventListener('click',function(){
    var pw=qs('#lockPw').value;
    if(!pw){ showLockError('请输入密码'); return; }
    unlock(pw, qs('#lockRemember').checked);
  });
  qs('#lockPw').addEventListener('keydown',function(e){
    if(e.key==='Enter'){ qs('#btnUnlock').click(); }
  });
  qs('#btnOfflineOpen').addEventListener('click',offlineOpen);

  qs('#btnSync').addEventListener('click',connectFile);
  qs('#btnReconnect').addEventListener('click',connectFile);
  qs('#bannerClose').addEventListener('click',function(){ qs('#syncBanner').hidden=true; });

  qs('#btnExport').addEventListener('click',exportData);
  qs('#btnImport').addEventListener('click',function(){ qs('#fileImport').click(); });
  qs('#fileImport').addEventListener('change',function(){
    var f=qs('#fileImport').files[0];
    qs('#fileImport').value='';
    if(f) importFile(f);
  });

  qs('#btnUseFile').addEventListener('click',function(){ qs('#modalConflict').hidden=true; resolveConflict('file'); });
  qs('#btnUseLocal').addEventListener('click',function(){ qs('#modalConflict').hidden=true; resolveConflict('local'); });
  qs('#btnCancelConflict').addEventListener('click',function(){ qs('#modalConflict').hidden=true; resolveConflict('cancel'); });

  document.querySelectorAll('.modal-overlay').forEach(function(ov){
    ov.addEventListener('mousedown',function(e){
      if(e.target===ov){
        ov.hidden=true;
        if(ov.id==='modalConflict') resolveConflict('cancel');
      }
    });
  });
  document.querySelectorAll('[data-close]').forEach(function(b){
    b.addEventListener('click',function(){ b.closest('.modal-overlay').hidden=true; });
  });
}

/* ================= 调试/测试接口（不影响正常使用） ================= */
window.__wb = {
  getState:function(){ return state; },
  addTask:function(t){
    state.tasks.push({
      id:uid(), title:String(t.title||''), note:String(t.note||''),
      due:t.due||null, priority:t.priority||'none', categoryId:t.categoryId||null,
      repeat:t.repeat||'none', done:false, createdAt:Date.now(), completedAt:null, updatedAt:Date.now(),
      subtasks:Array.isArray(t.subtasks)?t.subtasks.map(function(st){
        return {id:uid(), title:String(st.title||''), done:!!st.done, createdAt:Date.now(), completedAt:null};
      }):[]
    });
    saveState(); render();
  },
  clearAll:function(){ state=defaultState(); saveState(); render(); },
  test:{
    enc:encryptPayload,
    dec:decryptPayload,
    merge:mergeStates,
    b64urlEncode:b64urlEncode,
    b64urlDecode:b64urlDecode,
    setTombstone:function(k,v){ tombstones[k]=v; },
    cloud:function(){ return {enabled:cloud.enabled, sha:cloud.lastSha, dirty:cloud.dirty}; }
  }
};

/* ================= 启动 ================= */
function init(){
  loadState();
  bindEvents();
  render();
  qs('#btnTheme').textContent=THEME_ICON[state.settings.theme]||'🌓';
  setInterval(checkReminders,60*1000);
  setTimeout(checkReminders,1500);
  cloud.cfg=loadCloudConfig();
  renderCloudUI();
  if(cloud.cfg){
    var savedPw=null;
    try{ savedPw=localStorage.getItem(LS_CLOUD_PW); }catch(e){}
    if(savedPw){
      showLock('正在自动解锁…');
      unlock(savedPw, true);
    }else{
      showLock();
    }
  }else{
    setSyncStatus('off');
  }
  document.documentElement.setAttribute('data-ready','1');
}
init();

})();
</script>
</body>
</html>
