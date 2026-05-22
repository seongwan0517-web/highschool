# complete.html

```html
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>용유중 진학센터</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700;800&family=Noto+Serif+KR:wght@500;700&display=swap" rel="stylesheet">

<style>
:root {
  --navy:#0b1d3a;
  --navy-mid:#163260;
  --gold:#c9a84c;
  --gold-lt:#e8c97a;
  --cream:#f7f3eb;
  --white:#fff;
  --txt:#1a1a2e;
  --muted:#7a8499;
  --border:rgba(201,168,76,.2);
}

*{margin:0;padding:0;box-sizing:border-box;}

body{
  font-family:'Noto Sans KR',sans-serif;
  background:var(--cream);
  max-width:430px;
  margin:0 auto;
  min-height:100vh;
  color:var(--txt);
}

.site-header{
  padding:30px 20px 10px;
}

.badge{
  display:inline-block;
  background:var(--navy);
  color:var(--gold);
  font-size:10px;
  padding:6px 12px;
  border-radius:20px;
  font-weight:700;
}

.title{
  margin-top:12px;
  font-size:30px;
  color:var(--navy);
  font-family:'Noto Serif KR',serif;
  font-weight:700;
}

.title em{
  color:var(--gold);
  font-style:normal;
}

.subtitle{
  margin-top:6px;
  color:var(--muted);
  font-size:13px;
}

.page{
  display:none;
  padding:14px;
}

.page.show{
  display:block;
}

.card{
  background:#fff;
  border-radius:24px;
  padding:20px;
  margin-bottom:14px;
  box-shadow:0 10px 30px rgba(0,0,0,.06);
}

.card-hd{
  font-size:20px;
  font-family:'Noto Serif KR',serif;
  color:var(--navy);
  margin-bottom:18px;
  font-weight:700;
}

.step-lbl{
  font-size:11px;
  color:var(--gold);
  margin:16px 0 8px;
  font-weight:700;
}

.type-grid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:8px;
}

.type-btn{
  padding:12px;
  border-radius:14px;
  border:1px solid var(--border);
  background:#fff;
  text-align:center;
  cursor:pointer;
  font-size:13px;
  font-weight:600;
}

.type-btn.active{
  background:var(--navy);
  color:var(--gold-lt);
}

button{
  width:100%;
  border:none;
  border-radius:14px;
  padding:14px;
  margin-top:10px;
  cursor:pointer;
  font-weight:700;
}

.btn-primary{
  background:linear-gradient(135deg,var(--navy),var(--navy-mid));
  color:#fff;
}

.btn-gold{
  background:linear-gradient(135deg,var(--gold),var(--gold-lt));
  color:var(--navy);
}

.btn-soft{
  background:#eef1f7;
  color:var(--navy);
}

.btn-danger{
  background:#b91c1c;
  color:#fff;
}

input,select{
  width:100%;
  padding:13px;
  border-radius:12px;
  border:1px solid var(--border);
  margin-top:10px;
  font-family:'Noto Sans KR',sans-serif;
}

.result-item{
  padding:15px;
  border-radius:14px;
  border:1px solid var(--border);
  margin-top:10px;
  cursor:pointer;
  background:#fff;
}

.poster-box{
  min-height:250px;
  border-radius:16px;
  border:2px dashed var(--border);
  display:flex;
  justify-content:center;
  align-items:center;
  overflow:hidden;
  margin-top:14px;
}

.poster-box img{
  width:100%;
}

.poster-empty{
  color:#b5bdc8;
  font-size:13px;
}

.drop-zone{
  border:2px dashed var(--gold);
  border-radius:16px;
  padding:30px;
  text-align:center;
  margin-top:14px;
  cursor:pointer;
}

.drop-preview{
  width:100%;
  border-radius:16px;
  margin-top:12px;
  display:none;
}

.comment-item{
  padding:14px;
  border-radius:14px;
  background:#fff;
  border:1px solid var(--border);
  margin-top:10px;
}

.comment-name{
  font-weight:700;
  color:var(--navy);
  margin-bottom:6px;
}

.comment-date{
  font-size:11px;
  color:#999;
  margin-bottom:8px;
}

.comment-text{
  font-size:13px;
  line-height:1.6;
}

.favorite-tag{
  margin-top:10px;
  display:inline-block;
  background:#fff6db;
  color:#9c7412;
  padding:6px 10px;
  border-radius:20px;
  font-size:12px;
  font-weight:700;
}
</style>
</head>
<body>

<header class="site-header">
  <div class="badge">🎓 Yongyou Middle School</div>
  <div class="title">진학<em>센터</em></div>
  <div class="subtitle">고등학교 진학 정보를 쉽고 빠르게 확인하세요.</div>
</header>

<div class="page show" id="loginPage">
  <div class="card">
    <div class="card-hd">로그인</div>
    <button class="btn-gold" onclick="guestLogin()">학생 · 학부모 입장</button>
    <button class="btn-primary" onclick="openTeacherLogin()">교사 로그인</button>

    <div id="teacherLoginBox" style="display:none;margin-top:12px;">
      <input id="adminId" placeholder="아이디">
      <input id="adminPw" type="password" placeholder="비밀번호">
      <button class="btn-primary" onclick="teacherLogin()">로그인</button>
    </div>
  </div>
</div>

<div class="page" id="mainPage">

  <div class="card">
    <div class="card-hd">학교 찾기</div>

    <div class="step-lbl">STEP 01 · 학교 유형</div>
    <div class="type-grid" id="typeGrid"></div>

    <div class="step-lbl">STEP 02 · 지역 선택</div>
    <select id="regionSelect"></select>

    <div class="step-lbl">STEP 03 · 학교 검색</div>
    <input id="schoolSearchInput" placeholder="학교 이름 검색">

    <select id="schoolSelect"></select>

    <button class="btn-primary" onclick="searchSchool()">조회하기</button>
  </div>

  <div class="card">
    <div class="card-hd">조회 결과</div>
    <div id="resultBox">
      <div class="poster-empty">검색 결과가 없습니다.</div>
    </div>
  </div>

  <div class="card" id="teacherCard" style="display:none;">
    <div class="card-hd">교사 관리</div>

    <button class="btn-primary" onclick="openAddPage()">학교 추가</button>
    <button class="btn-primary" onclick="openPosterPage()">포스터 등록</button>
    <button class="btn-danger" onclick="logout()">로그아웃</button>
  </div>

</div>

<div class="page" id="detailPage">
  <div class="card">

    <div class="card-hd" id="detailTitle"></div>

    <div id="favoriteArea"></div>

    <div id="openDateBox"></div>

    <div class="poster-box" id="posterBox">
      <div class="poster-empty">등록된 포스터가 없습니다.</div>
    </div>

    <button class="btn-primary" id="homepageBtn" style="display:none;">학교 홈페이지</button>

    <div style="margin-top:24px;">
      <div class="card-hd">입학설명회 후기</div>

      <input id="commentName" placeholder="이름">
      <input id="commentText" placeholder="설명회 후기 작성">

      <button class="btn-primary" onclick="addComment()">댓글 등록</button>

      <div id="commentList"></div>
    </div>

    <button class="btn-soft" onclick="goMain()">← 목록으로</button>

  </div>
</div>

<div class="page" id="addPage">
  <div class="card">
    <div class="card-hd">학교 추가</div>

    <select id="addType"></select>
    <select id="addRegion"></select>

    <input id="addName" placeholder="학교 이름">
    <input id="addDate" placeholder="입학설명회 날짜 예: 2026-09-12">
    <input id="addHomepage" placeholder="학교 홈페이지 URL">

    <button class="btn-primary" onclick="addSchool()">학교 추가</button>

    <button class="btn-soft" onclick="goMain()">뒤로가기</button>
  </div>
</div>

<div class="page" id="posterPage">
  <div class="card">
    <div class="card-hd">포스터 등록</div>

    <select id="posterType"></select>
    <select id="posterRegion"></select>
    <select id="posterSchool"></select>

    <div class="drop-zone" id="dropZone">
      📂 포스터 업로드
    </div>

    <input type="file" id="fileInput" accept="image/*" style="display:none;">

    <img id="preview" class="drop-preview">

    <button class="btn-primary" onclick="savePoster()">포스터 저장</button>

    <button class="btn-soft" onclick="goMain()">뒤로가기</button>
  </div>
</div>

<script type="module">
import { initializeApp } from 'https://www.gstatic.com/firebasejs/10.12.2/firebase-app.js';

import {
  getDatabase,
  ref,
  set,
  push,
  onValue
} from 'https://www.gstatic.com/firebasejs/10.12.2/firebase-database.js';

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "highschool-d02c9.firebaseapp.com",
  databaseURL: "https://highschool-d02c9-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId: "highschool-d02c9",
  storageBucket: "highschool-d02c9.firebasestorage.app",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};

const app = initializeApp(firebaseConfig);
const db = getDatabase(app);

window.db = db;
window.ref = ref;
window.set = set;
window.push = push;
window.onValue = onValue;

const types = [
  '일반고','특성화고','마이스터고','특목고',
  '국제고&외국어고','자율고','예체고','과학고'
];

const regions = [
  '서울특별시','인천광역시','경기도','부산광역시'
];

let schools = [];
let selectedType = '일반고';
let selectedImage = '';
let currentSchool = '';

const defaultSchools = [
  {
    type:'일반고',
    region:'인천광역시',
    name:'인천영종고등학교',
    poster:'',
    openDate:'2026-09-12',
    homepage:'https://youngjong.icehs.kr'
  },
  {
    type:'특성화고',
    region:'인천광역시',
    name:'영종국제물류고등학교',
    poster:'',
    openDate:'2026-08-20',
    homepage:'https://youngjong.icehs.kr'
  },
  {
    type:'자율고',
    region:'인천광역시',
    name:'인천하늘고등학교',
    poster:'',
    openDate:'2026-10-01',
    homepage:'https://www.haneul.hs.kr'
  }
];

function showPage(id){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('show'));
  document.getElementById(id).classList.add('show');
}

window.guestLogin = function(){
  showPage('mainPage');
}

window.openTeacherLogin = function(){
  document.getElementById('teacherLoginBox').style.display='block';
}

window.teacherLogin = function(){
  const id = document.getElementById('adminId').value;
  const pw = document.getElementById('adminPw').value;

  if(id==='admin' && pw==='1234!'){
    document.getElementById('teacherCard').style.display='block';
    showPage('mainPage');
  } else {
    alert('로그인 실패');
  }
}

window.logout = function(){
  location.reload();
}

window.goMain = function(){
  showPage('mainPage');
}

function renderTypes(){
  document.getElementById('typeGrid').innerHTML = types.map(t=>`
    <div class="type-btn ${selectedType===t ? 'active':''}"
      onclick="selectType('${t}')">
      ${t}
    </div>
  `).join('');
}

window.selectType = function(type){
  selectedType = type;
  renderTypes();
  updateSchoolList();
}

function fillSelects(){

  const regionHTML = regions.map(r=>`<option>${r}</option>`).join('');

  ['regionSelect','addRegion','posterRegion']
  .forEach(id=>{
    document.getElementById(id).innerHTML = regionHTML;
  });

  const typeHTML = types.map(t=>`<option>${t}</option>`).join('');

  ['addType','posterType']
  .forEach(id=>{
    document.getElementById(id).innerHTML = typeHTML;
  });

  updateSchoolList();
  updatePosterSchools();
}

function updateSchoolList(){

  const region = document.getElementById('regionSelect').value;

  const keyword = document.getElementById('schoolSearchInput').value || '';

  const filtered = schools.filter(s=>
    s.type===selectedType &&
    s.region===region &&
    s.name.includes(keyword)
  );

  document.getElementById('schoolSelect').innerHTML =
    `<option value="">학교 선택</option>` +
    filtered.map(s=>`<option>${s.name}</option>`).join('');
}

function updatePosterSchools(){

  const type = document.getElementById('posterType').value;
  const region = document.getElementById('posterRegion').value;

  const filtered = schools.filter(s=>
    s.type===type &&
    s.region===region
  );

  document.getElementById('posterSchool').innerHTML =
    `<option value="">학교 선택</option>` +
    filtered.map(s=>`<option>${s.name}</option>`).join('');
}

window.searchSchool = function(){

  const name = document.getElementById('schoolSelect').value;

  if(!name){
    alert('학교를 선택하세요.');
    return;
  }

  document.getElementById('resultBox').innerHTML = `
    <div class="result-item" onclick="openDetail('${name}')">
      ${name}
    </div>
  `;
}

window.openDetail = function(name){

  currentSchool = name;

  showPage('detailPage');

  const school = schools.find(s=>s.name===name);

  document.getElementById('detailTitle').innerText = school.name;

  document.getElementById('posterBox').innerHTML = school.poster
    ? `<img src="${school.poster}">`
    : `<div class="poster-empty">등록된 포스터가 없습니다.</div>`;

  document.getElementById('openDateBox').innerHTML = `
    <div class="favorite-tag">
      📅 입학설명회 : ${school.openDate || '미정'}
    </div>
  `;

  const homepageBtn = document.getElementById('homepageBtn');

  if(school.homepage){
    homepageBtn.style.display='block';
    homepageBtn.onclick = ()=>window.open(school.homepage);
  } else {
    homepageBtn.style.display='none';
  }

  renderFavorite(name);
  loadComments(name);
}

function renderFavorite(name){

  const favorites = JSON.parse(localStorage.getItem('favorites')) || [];

  const isFavorite = favorites.includes(name);

  document.getElementById('favoriteArea').innerHTML = `
    <button class="btn-gold"
      onclick="toggleFavorite('${name}')">
      ${isFavorite ? '⭐ 즐겨찾기 완료':'☆ 즐겨찾기'}
    </button>
  `;
}

window.toggleFavorite = function(name){

  let favorites = JSON.parse(localStorage.getItem('favorites')) || [];

  if(favorites.includes(name)){
    favorites = favorites.filter(f=>f!==name);
  } else {
    favorites.push(name);
  }

  localStorage.setItem('favorites', JSON.stringify(favorites));

  renderFavorite(name);
}

window.openAddPage = function(){
  showPage('addPage');
}

window.addSchool = async function(){

  const school = {
    type:document.getElementById('addType').value,
    region:document.getElementById('addRegion').value,
    name:document.getElementById('addName').value.trim(),
    openDate:document.getElementById('addDate').value,
    homepage:document.getElementById('addHomepage').value,
    poster:''
  };

  if(!school.name){
    alert('학교명을 입력하세요.');
    return;
  }

  schools.push(school);

  await saveSchools();

  alert('학교 추가 완료');

  goMain();
}

window.openPosterPage = function(){
  showPage('posterPage');
}

window.savePoster = async function(){

  const schoolName = document.getElementById('posterSchool').value;

  if(!schoolName){
    alert('학교를 선택하세요.');
    return;
  }

  if(!selectedImage){
    alert('이미지를 업로드하세요.');
    return;
  }

  const school = schools.find(s=>s.name===schoolName);

  school.poster = selectedImage;

  await saveSchools();

  alert('포스터 저장 완료');
}

async function saveSchools(){
  await set(ref(db,'schools'), schools);
}

async function initSchools(){

  onValue(ref(db,'schools'), snapshot=>{

    const data = snapshot.val();

    if(data){
      schools = data;
    } else {
      schools = defaultSchools;
      saveSchools();
    }

    renderTypes();
    fillSelects();
  });
}

window.addComment = async function(){

  const name = document.getElementById('commentName').value.trim();
  const text = document.getElementById('commentText').value.trim();

  if(!name || !text){
    alert('댓글을 입력하세요.');
    return;
  }

  await push(ref(db, `comments/${currentSchool}`), {
    name,
    text,
    createdAt:new Date().toLocaleString('ko-KR')
  });

  document.getElementById('commentName').value='';
  document.getElementById('commentText').value='';
}

function loadComments(name){

  onValue(ref(db, `comments/${name}`), snapshot=>{

    const data = snapshot.val();

    const box = document.getElementById('commentList');

    if(!data){
      box.innerHTML = `
        <div class="poster-empty" style="margin-top:14px;">
          아직 등록된 후기가 없습니다.
        </div>
      `;
      return;
    }

    const comments = Object.values(data).reverse();

    box.innerHTML = comments.map(c=>`
      <div class="comment-item">
        <div class="comment-name">${c.name}</div>
        <div class="comment-date">${c.createdAt}</div>
        <div class="comment-text">${c.text}</div>
      </div>
    `).join('');
  });
}

const dropZone = document.getElementById('dropZone');
const fileInput = document.getElementById('fileInput');

dropZone.onclick = ()=>fileInput.click();

fileInput.onchange = function(){
  loadImage(this.files[0]);
}

dropZone.ondragover = e=>e.preventDefault();

dropZone.ondrop = e=>{
  e.preventDefault();
  loadImage(e.dataTransfer.files[0]);
}

function loadImage(file){

  const reader = new FileReader();

  reader.onload = e=>{

    selectedImage = e.target.result;

    const preview = document.getElementById('preview');

    preview.src = selectedImage;
    preview.style.display='block';
  }

  reader.readAsDataURL(file);
}

document.getElementById('regionSelect').onchange = updateSchoolList;
document.getElementById('schoolSearchInput').oninput = updateSchoolList;
document.getElementById('posterType').onchange = updatePosterSchools;
document.getElementById('posterRegion').onchange = updatePosterSchools;

initSchools();

</script>

</body>
</html>


