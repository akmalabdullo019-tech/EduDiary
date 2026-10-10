const state = {
  role: 'student',
  section: 'dashboard',
  darkMode: false,
};

const userProfiles = {
  student: {
    name: 'Aziza Axmedova',
    role: 'Talaba',
    school: '10-A sinf',
    avgGrade: '4.8',
    attendance: '96%',
    pendingHomework: '3 ta',
    welcome: 'Salom, Aziza! Bugun ko’p maqsadga erishdingiz.',
    subtitle: 'Bugungi dars jadvali, baholar va uy vazifalari zamonaviy nazorat panelida.'
  },
  teacher: {
    name: 'Nilufar Karimova',
    role: 'O`qituvchi',
    school: 'Matematika fani',
    avgGrade: '4.9',
    attendance: '98%',
    pendingHomework: '5 ta',
    welcome: 'Salom, Nilufar! Bugun sinflar natijalari va dars ishlanmalarini tekshirish kerak.',
    subtitle: 'Baholarni kiritish, davomatni ko’rish va uy vazifalarini nazorat qilish.'
  },
  parent: {
    name: 'Farhod Axmedov',
    role: 'Ota-ona',
    school: 'Farzand: Aziza',
    avgGrade: '4.7',
    attendance: '94%',
    pendingHomework: '2 ta',
    welcome: 'Salom, Farhod! Farzandingizning natijalari va davomatini kuzatib boring.',
    subtitle: 'Ota-onalar uchun yakuniy ko’rsatkichlar va eslatmalar.'
  },
  admin: {
    name: 'Sardor Adminov',
    role: 'Administrator',
    school: 'Maktab menejmenti',
    avgGrade: '4.9',
    attendance: '99%',
    pendingHomework: '7 ta',
    welcome: 'Salom, Sardor! Maktab faoliyatini kuzatib borish va boshqarish jarayoni boshqariladi.',
    subtitle: 'Foydalanuvchilar, fanlar, sinflar va umumiy statistikalar.'
  }
};

const statsByRole = {
  student: [
    { label: 'O’rtacha baho', value: '4.8', change: '+0.2', tone: 'success' },
    { label: 'Bugungi darslar', value: '5', change: '2 ta qoldi', tone: 'neutral' },
    { label: 'Uy vazifalari', value: '3', change: '1 ta kechikkan', tone: 'warning' },
    { label: 'Davomiylik', value: '96%', change: '+4%', tone: 'success' }
  ],
  teacher: [
    { label: 'Baholar', value: '128', change: '+18%', tone: 'success' },
    { label: 'Sinflar', value: '6', change: '4 ta faol', tone: 'neutral' },
    { label: 'Topshirishlar', value: '31', change: '12 ta tasdiqlandi', tone: 'warning' },
    { label: 'Davomiylik', value: '98%', change: '+2%', tone: 'success' }
  ],
  parent: [
    { label: 'Farzand bahosi', value: '4.7', change: '+0.1', tone: 'success' },
    { label: 'Darslar', value: '4', change: 'Bugun 4 ta', tone: 'neutral' },
    { label: 'Uy vazifalari', value: '2', change: '1 ta ko’rib chiqilmagan', tone: 'warning' },
    { label: 'Davomiylik', value: '94%', change: '-1%', tone: 'danger' }
  ],
  admin: [
    { label: 'Talabalar', value: '842', change: '+34', tone: 'success' },
    { label: 'O’qituvchilar', value: '76', change: '+4', tone: 'neutral' },
    { label: 'Sinflar', value: '22', change: '5 ta yangi', tone: 'warning' },
    { label: 'Aktivlik', value: '92%', change: '+7%', tone: 'success' }
  ]
};

const gradeData = [
  { subject: 'Matematika', teacher: 'Nilufar Karimova', grade: '5', type: 'Test', date: '12.10.2026', comment: 'Yuqori natija' },
  { subject: 'Fizika', teacher: 'Javohir Aliyev', grade: '4', type: 'Laboratoriya', date: '10.10.2026', comment: 'Tushuntirishga e’tibor qaratish' },
  { subject: 'Biologiya', teacher: 'Mavluda Sodiqova', grade: '5', type: 'Nazorat', date: '08.10.2026', comment: 'Ajoyib' },
  { subject: 'Tarix', teacher: 'Ravshan Xasanov', grade: '4', type: 'Savol-javob', date: '06.10.2026', comment: 'Qisqa javoblar yaxshi' }
];

const timetableData = [
  {
    day: 'Dushanba',
    slots: [
      { time: '08:30-09:15', subject: 'Matematika', room: 'A-204' },
      { time: '09:30-10:15', subject: 'Fizika', room: 'B-104' },
      { time: '10:30-11:15', subject: 'Ingliz tili', room: 'C-102' }
    ]
  },
  {
    day: 'Seshanba',
    slots: [
      { time: '08:30-09:15', subject: 'Biologiya', room: 'A-118' },
      { time: '09:30-10:15', subject: 'Tarix', room: 'D-212' },
      { time: '10:30-11:15', subject: 'Kimyo', room: 'Lab-3' }
    ]
  },
  {
    day: 'Chorshanba',
    slots: [
      { time: '08:30-09:15', subject: 'Geometriya', room: 'A-204' },
      { time: '09:30-10:15', subject: 'Adabiyot', room: 'C-117' },
      { time: '10:30-11:15', subject: 'Fizika', room: 'B-104' }
    ]
  }
];

const homeworkData = [
  { title: 'Matematika: tenglamalarni yechish', status: 'pending', due: 'Bugun, 18:00' },
  { title: 'Fizika: 3-mavzu notes', status: 'done', due: 'Ertaga, 15:00' },
  { title: 'Biologiya: tezis tayyorlash', status: 'overdue', due: 'Kecha, 20:00' }
];

const attendanceData = [
  { month: 'Sentabr', value: 96 },
  { month: 'Oktabr', value: 98 },
  { month: 'Noyabr', value: 94 },
  { month: 'Dekabr', value: 97 }
];

const messagesData = [
  { name: 'Nilufar Karimova', preview: 'Bahoni kiritdim, tekshirib ko’ring.' },
  { name: 'Maktab boshqaruvi', preview: 'Yangi e’lonlar ma’lum qilindi.' },
  { name: 'Farhod Axmedov', preview: 'Farzandingizning natijalariga qarang.' }
];

const announcementsData = [
  { title: 'Maktab bayrami', text: '28-oktabr kuni maktab umumiy tadbirga mezbonlik qiladi.', date: '12 oktyabr' },
  { title: 'Sinov natijalari', text: '1-chorak yakunlari 21-oktabrda e’lon qilinadi.', date: '10 oktyabr' },
  { title: 'Yangi dars jadvallari', text: 'Jadvaldagi o’zgarishlar ma’muriyat qarori asosida amaliyotga kiritildi.', date: '08 oktyabr' }
];

const adminUsers = [
  { user: 'Aziza Axmedova', role: 'Talaba', status: 'Faol', activity: '12 daqiqa oldin' },
  { user: 'Nilufar Karimova', role: 'O`qituvchi', status: 'Faol', activity: '25 daqiqa oldin' },
  { user: 'Farhod Axmedov', role: 'Ota-ona', status: 'Yangi', activity: '1 soat oldin' },
  { user: 'Sardor Adminov', role: 'Administrator', status: 'Faol', activity: 'Hozir' }
];

const dailyLessons = [
  { time: '8:30 - 9:15', subject: 'Matematika', room: 'A-204' },
  { time: '9:30 - 10:15', subject: 'Fizika', room: 'B-104' },
  { time: '10:30 - 11:15', subject: 'Ingliz tili', room: 'C-402' }
];

const recentGrades = [
  { subject: 'Matematika', grade: '5.0', tag: 'good' },
  { subject: 'Fizika', grade: '4.5', tag: 'medium' },
  { subject: 'Biologiya', grade: '5.0', tag: 'good' }
];

function renderStats() {
  const statsContainer = document.getElementById('statsGrid');
  const stats = statsByRole[state.role];
  statsContainer.innerHTML = stats.map(
    (item) => `
      <div class="stat-card">
        <div class="stat-top">
          <h3>${item.label}</h3>
          <span class="badge ${item.tone}">${item.change}</span>
        </div>
        <strong>${item.value}</strong>
        <div class="small-change">Oylik ko’rsatkich</div>
      </div>
    `
  ).join('');
}

function renderLessons() {
  const list = document.getElementById('todayLessons');
  list.innerHTML = dailyLessons.map((lesson) => `
    <div class="lesson-item">
      <div class="left">
        <div class="lesson-icon">${lesson.subject.slice(0, 1)}</div>
        <div>
          <strong>${lesson.subject}</strong>
          <small>${lesson.room}</small>
        </div>
      </div>
      <div>
        <small>${lesson.time}</small>
      </div>
    </div>
  `).join('');
}

function renderRecentGrades() {
  const list = document.getElementById('recentGrades');
  list.innerHTML = recentGrades.map((item) => `
    <div class="grade-item">
      <div class="left">
        <div class="topic-icon">${item.subject.slice(0, 1)}</div>
        <div>
          <strong>${item.subject}</strong>
          <small>Bugungi baho</small>
        </div>
      </div>
      <span class="grade-badge ${item.tag}">${item.grade}</span>
    </div>
  `).join('');
}

function renderWeeklyChart() {
  const chart = document.getElementById('weeklyChart');
  const values = [78, 82, 88, 86, 91, 94, 96];
  const labels = ['Du', 'Se', 'Ch', 'Pa', 'Ju', 'Sh', 'Ya'];

  chart.innerHTML = labels.map((label, index) => `
    <div class="bar-col">
      <div class="bar" style="height: ${values[index]}%"></div>
      <span class="bar-label">${label}</span>
    </div>
  `).join('');
}

function renderAnnouncements() {
  const list = document.getElementById('announcementsList');
  list.innerHTML = announcementsData.slice(0, 3).map((item) => `
    <div class="news-item">
      <div class="left">
        <div class="topic-icon">📣</div>
        <div>
          <strong>${item.title}</strong>
          <small>${item.date}</small>
        </div>
      </div>
    </div>
  `).join('');

  const full = document.getElementById('fullAnnouncements');
  full.innerHTML = announcementsData.map((item) => `
    <div class="announcement-item">
      <div class="topic-icon">📢</div>
      <div>
        <h3>${item.title}</h3>
        <p>${item.text}</p>
        <small>${item.date}</small>
      </div>
    </div>
  `).join('');
}

function renderGradesTable() {
  const tbody = document.getElementById('gradeTable');
  tbody.innerHTML = gradeData.map((row) => `
    <tr>
      <td>${row.subject}</td>
      <td>${row.teacher}</td>
      <td><span class="grade-badge ${row.grade >= 4 ? 'good' : 'medium'}">${row.grade}</span></td>
      <td>${row.type}</td>
      <td>${row.date}</td>
      <td>${row.comment}</td>
    </tr>
  `).join('');
}

function renderTimetable() {
  const grid = document.getElementById('timetableGrid');
  grid.innerHTML = timetableData.map((day) => `
    <div class="schedule-card">
      <h3>${day.day}</h3>
      ${day.slots.map((slot) => `
        <div class="schedule-slot">
          <div>
            <strong>${slot.subject}</strong>
            <small>${slot.room}</small>
          </div>
          <small>${slot.time}</small>
        </div>
      `).join('')}
    </div>
  `).join('');
}

function renderHomework() {
  const list = document.getElementById('homeworkList');
  list.innerHTML = homeworkData.map((item) => `
    <div class="todo-item">
      <div class="left">
        <div class="lesson-icon">📝</div>
        <div class="meta">
          <strong>${item.title}</strong>
          <small>Muddat: ${item.due}</small>
        </div>
      </div>
      <span class="status-pill ${item.status}">${item.status === 'pending' ? 'Kutilmoqda' : item.status === 'done' ? 'Bajarildi' : 'Muddat o’tdi'}</span>
    </div>
  `).join('');
}

function renderAttendance() {
  const grid = document.getElementById('attendanceList');
  grid.innerHTML = attendanceData.map((item) => `
    <div class="attendance-card">
      <h3>${item.month}</h3>
      <div class="attendance-ring"><span>${item.value}%</span></div>
      <div class="small-change">Davomiylik foizi</div>
    </div>
  `).join('');
}

function renderMessages() {
  const sidebar = document.getElementById('messagesSidebar');
  sidebar.innerHTML = messagesData.map((item) => `
    <div class="message-item">
      <div class="left">
        <div class="chat-avatar">${item.name.slice(0, 1)}</div>
        <div>
          <strong>${item.name}</strong>
          <small>${item.preview}</small>
        </div>
      </div>
    </div>
  `).join('');

  const chatBox = document.getElementById('chatBox');
  chatBox.innerHTML = `
    <div class="chat-thread">
      <div class="chat-message">Salom! Baholarni tekshirish uchun tayyor.</div>
      <div class="chat-message me">Rahmat, ko’rsatkichlarni ko’rib chiqaman.</div>
    </div>
    <div class="chat-input">
      <input type="text" placeholder="Xabar yozing..." />
      <button class="primary-btn small-btn">Yuborish</button>
    </div>
  `;
}

function renderAdminStats() {
  const stats = document.getElementById('adminStats');
  stats.innerHTML = [
    { label: 'Talabalar', value: '842', tone: 'success' },
    { label: 'O’qituvchilar', value: '76', tone: 'neutral' },
    { label: 'Fanlar', value: '18', tone: 'warning' },
    { label: 'Maktab holati', value: 'Yaxshi', tone: 'success' }
  ].map((item) => `
    <div class="stat-card">
      <div class="stat-top">
        <h3>${item.label}</h3>
        <span class="badge ${item.tone}">${item.value}</span>
      </div>
      <strong>${item.value}</strong>
    </div>
  `).join('');

  const table = document.getElementById('adminTable');
  table.innerHTML = adminUsers.map((item) => `
    <tr>
      <td>${item.user}</td>
      <td>${item.role}</td>
      <td><span class="status-pill ${item.status === 'Faol' ? 'done' : 'pending'}">${item.status}</span></td>
      <td>${item.activity}</td>
    </tr>
  `).join('');
}

function setRole(role) {
  state.role = role;
  const profile = userProfiles[role];
  document.getElementById('headerName').textContent = profile.name;
  document.getElementById('headerRole').textContent = profile.role;
  document.getElementById('welcomeTitle').textContent = profile.welcome;
  document.getElementById('welcomeText').textContent = profile.subtitle;
  document.getElementById('avgGrade').textContent = profile.avgGrade;
  document.getElementById('attendanceStat').textContent = profile.attendance;
  document.getElementById('pendingHomework').textContent = profile.pendingHomework;
  renderStats();
}

function showSection(section) {
  state.section = section;

  document.querySelectorAll('.nav-item').forEach((btn) => {
    btn.classList.toggle('active', btn.dataset.section === section);
  });

  document.querySelectorAll('.content-section').forEach((el) => {
    el.classList.toggle('active', el.id === `${section}-section`);
  });

  const titles = {
    dashboard: ['Boshqaruv paneli', 'Bugungi faoliyat va umumiy ko’rsatkichlar'],
    grades: ['Baholar', 'Fan bo’yicha baholar va natijalar'],
    timetable: ['Jadvallar', 'Dars jadvali va faoliyat rejalari'],
    homework: ['Uy vazifalari', 'Topshirish, tekshirish va nazorat'],
    attendance: ['Davomiylik', 'O’quvchilar va sinf statistikasi'],
    messages: ['Xabarlar', 'Ichki aloqa va ogohlantirishlar'],
    announcements: ['E’lonlar', 'Maktab yangiliklari va bildirishnomalar'],
    admin: ['Admin paneli', 'Maktab boshqaruvi va statistika']
  };

  document.getElementById('page-title').textContent = titles[section][0];
  document.getElementById('page-subtitle').textContent = titles[section][1];
}

function attachEvents() {
  document.querySelectorAll('.nav-item').forEach((item) => {
    item.addEventListener('click', () => showSection(item.dataset.section));
  });

  document.querySelectorAll('.demo-btn').forEach((btn) => {
    btn.addEventListener('click', () => setRole(btn.dataset.role));
  });

  document.querySelectorAll('.primary-btn[data-section]').forEach((btn) => {
    btn.addEventListener('click', () => showSection(btn.dataset.section));
  });

  document.getElementById('themeToggle').addEventListener('click', () => {
    document.body.classList.toggle('dark');
    state.darkMode = !state.darkMode;
    document.getElementById('themeToggle').textContent = state.darkMode ? '☀️' : '🌙';
  });
}

function init() {
  attachEvents();
  setRole('student');
  showSection('dashboard');
  renderLessons();
  renderRecentGrades();
  renderWeeklyChart();
  renderAnnouncements();
  renderGradesTable();
  renderTimetable();
  renderHomework();
  renderAttendance();
  renderMessages();
  renderAdminStats();
}

init();
