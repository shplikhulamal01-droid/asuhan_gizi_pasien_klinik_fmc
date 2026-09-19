<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Asuhan Gizi Pasien - Klinik FMC</title>
<style>
:root{--primary:#087f5b;--light:#e9f7f1;--border:#cbd5e1;--text:#1f2937;--muted:#64748b}
*{box-sizing:border-box}
body{margin:0;font-family:Arial,Helvetica,sans-serif;background:#f3f6f8;color:var(--text);line-height:1.45}
.container{max-width:1100px;margin:24px auto;padding:0 16px}
header{background:linear-gradient(135deg,#087f5b,#0ca678);color:white;padding:26px;border-radius:16px 16px 0 0}
header h1{margin:0 0 5px;font-size:27px}
header p{margin:0;opacity:.95}
.card{background:#fff;border:1px solid #e2e8f0;border-radius:14px;padding:20px;margin:16px 0;box-shadow:0 3px 12px #0f172a0b}
h2{font-size:19px;margin:0 0 16px;color:var(--primary);border-bottom:2px solid var(--light);padding-bottom:9px}
h3{font-size:15px;margin:18px 0 10px;color:#334155}
.grid{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:13px}
.field{display:flex;flex-direction:column;gap:5px}
.field.full{grid-column:1/-1}
label{font-weight:600;font-size:13px}
input,select,textarea{width:100%;padding:10px 11px;border:1px solid var(--border);border-radius:8px;font:inherit;background:#fff}
textarea{min-height:78px;resize:vertical}
input:focus,select:focus,textarea:focus{outline:2px solid #99e9c9;border-color:var(--primary)}
.result{background:var(--light);padding:12px;border-radius:10px;font-weight:700}
.actions{display:flex;gap:10px;flex-wrap:wrap;margin:18px 0}
button{border:0;border-radius:9px;padding:12px 17px;font-weight:700;cursor:pointer;font-size:14px}
.primary{background:var(--primary);color:white}
.secondary{background:#e2e8f0;color:#1e293b}
.danger{background:#fee2e2;color:#991b1b}
.small{font-size:12px;color:var(--muted)}
.signature{min-height:100px}
.footer{text-align:center;color:var(--muted);font-size:12px;padding:15px}
@media(max-width:760px){.grid{grid-template-columns:1fr 1fr}.field.full{grid-column:1/-1}}
@media(max-width:480px){.grid{grid-template-columns:1fr}header h1{font-size:22px}}
@media print{
 body{background:white}.container{max-width:none;margin:0;padding:0}
 header{color:#000;background:white;border:2px solid #000;border-radius:0}
 .card{box-shadow:none;border:1px solid #999;break-inside:avoid}
 .actions,.no-print{display:none!important}
 input,select,textarea{border:0;padding:3px;background:white}
 h2{color:#000}
}
</style>
</head>
<body>
<div class="container">
<header>
<h1>ASUHAN GIZI PASIEN</h1>
<p>Klinik Pratama Rawat Inap Family Medical Care (FMC)</p>
<p class="small" style="color:white">Formulir dokumentasi proses asuhan gizi pasien</p>
</header>

<form id="nutritionForm">
<section class="card">
<h2>1. Identitas Pasien</h2>
<div class="grid">
<div class="field"><label>Nomor Rekam Medis</label><input name="rm" required></div>
<div class="field"><label>Nama Pasien</label><input name="nama" required></div>
<div class="field"><label>Tanggal Asuhan</label><input type="date" name="tanggal" id="tanggal" required></div>
<div class="field"><label>Tanggal Lahir</label><input type="date" name="lahir" id="lahir"></div>
<div class="field"><label>Umur (tahun)</label><input type="number" name="umur" id="umur" min="0"></div>
<div class="field"><label>Jenis Kelamin</label><select name="jk"><option value="">Pilih</option><option>Laki-laki</option><option>Perempuan</option></select></div>
<div class="field"><label>Ruangan/Poli</label><input name="ruangan"></div>
<div class="field"><label>Diagnosis Medis</label><input name="diagnosis_medis"></div>
<div class="field"><label>Diet Sebelumnya</label><input name="diet_sebelumnya"></div>
</div>
</section>

<section class="card">
<h2>2. Assessment / Pengkajian Gizi</h2>
<h3>Antropometri</h3>
<div class="grid">
<div class="field"><label>Berat Badan Saat Ini (kg)</label><input type="number" step="0.1" id="bb" name="bb"></div>
<div class="field"><label>Tinggi Badan (cm)</label><input type="number" step="0.1" id="tb" name="tb"></div>
<div class="field"><label>Berat Badan Usual (kg)</label><input type="number" step="0.1" id="bbu" name="bbu"></div>
<div class="field"><label>Penurunan/Peningkatan BB (kg)</label><input type="number" step="0.1" name="perubahan_bb"></div>
<div class="field"><label>Lingkar Lengan Atas (cm)</label><input type="number" step="0.1" name="lila"></div>
<div class="field"><label>IMT</label><div class="result" id="imtResult">-</div></div>
<div class="field full"><label>Status Gizi / Interpretasi Antropometri</label><input id="statusGizi" name="status_gizi" readonly></div>
</div>

<h3>Biokimia / Laboratorium</h3>
<div class="grid">
<div class="field full"><label>Hasil Laboratorium</label><textarea name="lab" placeholder="Contoh: Hb, leukosit, albumin, GDP, ureum, kreatinin, elektrolit, dll."></textarea></div>
</div>

<h3>Klinis / Fisik</h3>
<div class="grid">
<div class="field"><label>Nafsu Makan</label><select name="nafsu"><option value="">Pilih</option><option>Baik</option><option>Menurun</option><option>Meningkat</option></select></div>
<div class="field"><label>Keluhan Gastrointestinal</label><input name="gastro" placeholder="Mual, muntah, diare, konstipasi..."></div>
<div class="field"><label>Kondisi Khusus</label><input name="kondisi_khusus" placeholder="Demam, luka, edema, dll."></div>
<div class="field full"><label>Pemeriksaan Fisik/Klinis Lainnya</label><textarea name="klinis"></textarea></div>
</div>

<h3>Riwayat Makan dan Faktor Lain</h3>
<div class="grid">
<div class="field full"><label>Asupan Makan / Recall 24 Jam</label><textarea name="recall"></textarea></div>
<div class="field full"><label>Alergi / Pantangan Makanan</label><textarea name="alergi"></textarea></div>
<div class="field full"><label>Riwayat Penyakit / Obat</label><textarea name="riwayat"></textarea></div>
<div class="field full"><label>Faktor Sosial, Ekonomi, dan Pengetahuan Gizi</label><textarea name="sosial"></textarea></div>
</div>
</section>

<section class="card">
<h2>3. Perhitungan Kebutuhan Gizi</h2>
<p class="small">Pilih kondisi/tujuan pasien. Sistem akan memberikan estimasi awal. Hasil harus divalidasi dan disesuaikan oleh nutrisionis/dietisien berdasarkan kondisi klinis dan SOP.</p>
<div class="grid">
<div class="field"><label>Metode Perhitungan</label><select id="metodeEnergi" name="metode_energi" onchange="calculate()">
<option value="25">25 kkal/kg BB - umum</option>
<option value="30">30 kkal/kg BB - kebutuhan lebih tinggi</option>
<option value="35">35 kkal/kg BB - kebutuhan tinggi</option>
<option value="custom">Manual</option>
</select></div>
<div class="field"><label>Tujuan/Kondisi</label><select id="tujuanGizi" name="tujuan_gizi" onchange="autoNutritionPreset()">
<option value="general">Umum / pemeliharaan</option>
<option value="weightloss">Penurunan BB</option>
<option value="gain">Peningkatan BB</option>
<option value="tktp">TKTP / kebutuhan protein tinggi</option>
<option value="elderly">Lansia</option>
<option value="custom">Kustom</option>
</select></div>
<div class="field"><label>Faktor Aktivitas</label><select id="aktivitas" name="aktivitas" onchange="calculate()"><option value="1.2">1,2 - Bed rest</option><option value="1.3">1,3 - Aktivitas ringan</option><option value="1.4">1,4 - Aktivitas sedang</option><option value="1.5">1,5 - Aktivitas tinggi</option></select></div>
<div class="field"><label>Faktor Stres</label><select id="stres" name="stres" onchange="calculate()"><option value="1">1,0 - Tidak ada</option><option value="1.1">1,1 - Ringan</option><option value="1.2">1,2 - Sedang</option><option value="1.3">1,3 - Berat</option></select></div>
<div class="field"><label>Protein (g/kg BB)</label><input type="number" step="0.1" id="proteinKg" name="protein_kg" value="1.0" oninput="calculate()"></div>
<div class="field"><label>Target Energi Manual (kkal/hari)</label><input type="number" id="energiManual" name="energi_manual" placeholder="Opsional" oninput="calculate()"></div>
<div class="field"><label>Kebutuhan Energi</label><div class="result" id="energiResult">-</div></div>
<div class="field"><label>Kebutuhan Protein</label><div class="result" id="proteinResult">-</div></div>
<div class="field"><label>Estimasi Lemak</label><div class="result" id="lemakResult">-</div></div>
<div class="field"><label>Estimasi Karbohidrat</label><div class="result" id="karboResult">-</div></div>
<div class="field full"><label>Preskripsi Energi/Protein Otomatis</label><textarea name="preskripsi_otomatis" id="preskripsiOtomatis" readonly></textarea></div>
<div class="field full"><label>Catatan Perhitungan</label><textarea name="catatan_perhitungan" id="catatanPerhitungan">Estimasi energi = kebutuhan dasar kkal/kg BB × faktor aktivitas × faktor stres. Protein = BB × target protein g/kg. Lemak dan karbohidrat merupakan estimasi dari distribusi energi 25% lemak dan 55% karbohidrat.</textarea></div>
</div>
</section>

<section class="card">
<h2>4. Diagnosis Gizi</h2>
<div class="grid">
<div class="field full"><label>Pilih Masalah Gizi</label>
<select id="diagnosisOption" name="diagnosis_option" onchange="autoDiagnosis()">
<option value="">-- Pilih diagnosis --</option>
<option value="energy">Asupan energi tidak adekuat</option>
<option value="protein">Asupan protein tidak adekuat</option>
<option value="excess">Asupan energi berlebih</option>
<option value="weightloss">Penurunan berat badan tidak diharapkan</option>
<option value="overweight">Kelebihan berat badan</option>
<option value="knowledge">Kurang pengetahuan terkait gizi</option>
<option value="fluid">Asupan cairan tidak adekuat</option>
<option value="fiber">Asupan serat tidak adekuat</option>
<option value="intake">Asupan oral tidak adekuat</option>
<option value="custom">Diagnosis lain / manual</option>
</select></div>
<div class="field full"><label>Problem (P) / Masalah Gizi</label><textarea name="problem" id="problem"></textarea></div>
<div class="field full"><label>Etiology (E) / Penyebab</label><textarea name="etiology" id="etiology"></textarea></div>
<div class="field full"><label>Signs & Symptoms (S) / Tanda dan Gejala</label><textarea name="signs" id="signs"></textarea></div>
<div class="field full"><label>Diagnosis Gizi Format PES</label><textarea name="pes" id="pes" placeholder="Akan terisi otomatis dan dapat diedit."></textarea></div>
</div>
</section>

<section class="card">
<h2>5. Intervensi Gizi</h2>
<div class="grid">
<div class="field"><label>Jenis Diet</label><select name="jenis_diet" id="jenisDiet" onchange="autoIntervention()">
<option value="">-- Pilih jenis diet --</option><option>Diet Normal</option><option>Diet TKTP</option><option>Diet Diabetes Melitus</option><option>Diet Rendah Garam</option><option>Diet Rendah Lemak</option><option>Diet Rendah Protein</option><option>Diet Tinggi Protein</option><option>Diet Rendah Serat</option><option>Diet Tinggi Serat</option><option>Diet Jantung</option><option>Diet Ginjal</option><option>Diet Hati</option><option>Diet Rendah Purin</option><option>Diet Rendah Laktosa</option><option>Diet Lunak</option><option>Diet Cair</option><option>Diet Kombinasi / Kustom</option>
</select></div>
<div class="field"><label>Bentuk Makanan</label><select name="bentuk"><option value="">Pilih</option><option>Biasa</option><option>Lunak</option><option>Saring</option><option>Cair</option><option>Enteral</option><option>Parenteral</option></select></div>
<div class="field"><label>Frekuensi Makan</label><select name="frekuensi"><option value="">Pilih</option><option>3x makan utama</option><option>3x makan + 1x snack</option><option>3x makan + 2x snack</option><option>Porsi kecil tapi sering</option><option>Sesuai toleransi</option></select></div>
<div class="field"><label>Strategi Intervensi</label><select name="strategi_intervensi" id="strategiIntervensi" onchange="autoIntervention()">
<option value="">-- Pilih --</option><option>Memenuhi kebutuhan energi dan protein</option><option>Meningkatkan asupan makan</option><option>Mengurangi asupan energi</option><option>Meningkatkan kualitas pola makan</option><option>Mengatur jenis dan jumlah karbohidrat</option><option>Mengurangi natrium/garam</option><option>Meningkatkan asupan protein</option><option>Menyesuaikan cairan</option><option>Meningkatkan asupan serat</option><option>Modifikasi tekstur makanan</option><option>Edukasi dan konseling gizi</option>
</select></div>
<div class="field full"><label>Tujuan Intervensi</label><textarea name="tujuan_intervensi" id="tujuanIntervensi"></textarea></div>
<div class="field full"><label>Preskripsi / Modifikasi Diet</label><textarea name="preskripsi" id="preskripsiIntervensi"></textarea></div>
<div class="field full"><label>Edukasi dan Konseling Gizi</label><textarea name="edukasi" id="edukasiIntervensi"></textarea></div>
<div class="field full"><label>Kolaborasi / Rujukan</label><textarea name="kolaborasi"></textarea></div>
</div>
</section>

<section class="card">
<h2>6. Monitoring dan Evaluasi</h2>
<div class="grid">
<div class="field"><label>Parameter Utama</label><select name="parameter" id="parameterMonev" onchange="autoMonev()">
<option value="">-- Pilih parameter --</option><option>Asupan energi</option><option>Asupan protein</option><option>Asupan makanan (%)</option><option>Berat badan</option><option>IMT</option><option>Lingkar Lengan Atas</option><option>Keluhan gastrointestinal</option><option>Gula darah</option><option>Tekanan darah</option><option>Hasil laboratorium</option><option>Status hidrasi</option><option>Kepatuhan diet</option><option>Pengetahuan gizi</option><option>Kondisi klinis</option><option>Parameter lainnya</option>
</select></div>
<div class="field"><label>Frekuensi Monitoring</label><select name="frekuensi_monitoring"><option>Harian</option><option>Setiap shift</option><option>2–3 hari</option><option>Mingguan</option><option>Sesuai kondisi pasien</option></select></div>
<div class="field"><label>Target Evaluasi</label><select name="target" id="targetMonev" onchange="autoMonev()">
<option value="">-- Pilih target --</option><option>Asupan ≥ 80% kebutuhan</option><option>Asupan ≥ 90% kebutuhan</option><option>Berat badan stabil</option><option>Berat badan meningkat bertahap</option><option>Berat badan menurun bertahap</option><option>Keluhan membaik</option><option>Parameter laboratorium membaik</option><option>Pasien patuh terhadap diet</option><option>Pasien mampu menjelaskan kembali edukasi</option><option>Target individual</option>
</select></div>
<div class="field"><label>Waktu Evaluasi</label><select name="waktu_evaluasi"><option>24 jam</option><option>48 jam</option><option>72 jam</option><option>1 minggu</option><option>Sesuai kondisi pasien</option></select></div>
<div class="field full"><label>Hasil Monitoring dan Evaluasi</label><textarea name="hasil_evaluasi" id="hasilEvaluasi" placeholder="Catat hasil aktual: asupan %, perubahan BB, keluhan, hasil lab, kepatuhan, dll."></textarea></div>
<div class="field full"><label>Kesimpulan Evaluasi</label><select name="kesimpulan_evaluasi"><option value="">-- Pilih --</option><option>Tujuan tercapai</option><option>Tujuan tercapai sebagian</option><option>Tujuan belum tercapai</option><option>Kondisi membaik</option><option>Kondisi belum membaik</option><option>Perlu evaluasi lanjutan</option></select></div>
<div class="field full"><label>Tindak Lanjut</label><textarea name="tindak_lanjut" id="tindakLanjut" placeholder="Akan dapat diisi berdasarkan hasil evaluasi."></textarea></div>
</div>
</section>

<section class="card">
<h2>7. Petugas</h2>
<div class="grid">
<div class="field"><label>Nama Nutrisionis/Dietisien</label><input name="petugas"></div>
<div class="field"><label>No. STR/SIP (jika diperlukan)</label><input name="str_sip"></div>
<div class="field"><label>Tanggal Pengisian</label><input type="date" name="tanggal_pengisian" id="tanggal_pengisian"></div>
<div class="field full"><label>Catatan Tambahan</label><textarea name="catatan"></textarea></div>
</div>
</section>

<div class="actions no-print">
<button type="button" class="primary" onclick="saveData()">Simpan Data di Browser</button>
<button type="button" class="secondary" onclick="loadData()">Muat Data Tersimpan</button>
<button type="button" class="secondary" onclick="window.print()">Cetak / Simpan PDF</button>
<button type="reset" class="danger" onclick="resetForm()">Reset Form</button>
</div>
</form>
<div class="footer">Klinik FMC • Formulir Asuhan Gizi Pasien • Gunakan sesuai SOP dan validasi tenaga kesehatan.</div>
</div>

<script>
const form=document.getElementById('nutritionForm');
const today=new Date().toISOString().split('T')[0];
document.getElementById('tanggal').value=today;
document.getElementById('tanggal_pengisian').value=today;

function calculate(){
 const bb=parseFloat(document.getElementById('bb').value);
 const tb=parseFloat(document.getElementById('tb').value);
 const metode=document.getElementById('metodeEnergi').value;
 const aktivitas=parseFloat(document.getElementById('aktivitas').value)||1;
 const stres=parseFloat(document.getElementById('stres').value)||1;
 const proteinKg=parseFloat(document.getElementById('proteinKg').value)||0;
 const manual=parseFloat(document.getElementById('energiManual').value);
 if(bb>0 && tb>0){
   const imt=bb/Math.pow(tb/100,2);
   document.getElementById('imtResult').textContent=imt.toFixed(2);
   let status=imt<17?'Sangat kurus':imt<18.5?'Kurus':imt<25?'Normal':imt<27?'Gemuk':'Obesitas';
   document.getElementById('statusGizi').value=status;
 }else{
   document.getElementById('imtResult').textContent='-';
   document.getElementById('statusGizi').value='';
 }
 if(bb>0){
   let dasar=metode==='custom' ? 0 : parseFloat(metode);
   let energi=(manual>0?manual:dasar*bb*aktivitas*stres);
   if(energi>0){
     const protein=bb*proteinKg, lemak=energi*.25/9, karbo=energi*.55/4;
     document.getElementById('energiResult').textContent=Math.round(energi)+' kkal/hari';
     document.getElementById('proteinResult').textContent=protein.toFixed(1)+' g/hari';
     document.getElementById('lemakResult').textContent=lemak.toFixed(1)+' g/hari';
     document.getElementById('karboResult').textContent=karbo.toFixed(1)+' g/hari';
     document.getElementById('preskripsiOtomatis').value='Energi ± '+Math.round(energi)+' kkal/hari; Protein ± '+protein.toFixed(1)+' g/hari; Lemak ± '+lemak.toFixed(1)+' g/hari; Karbohidrat ± '+karbo.toFixed(1)+' g/hari.';
   }
 }else{
   ['energiResult','proteinResult','lemakResult','karboResult'].forEach(id=>document.getElementById(id).textContent='-');
   document.getElementById('preskripsiOtomatis').value='';
 }
}
function autoNutritionPreset(){
 const tujuan=document.getElementById('tujuanGizi').value;
 const pk=document.getElementById('proteinKg');
 if(tujuan==='weightloss'){document.getElementById('metodeEnergi').value='25';pk.value='1.0';}
 else if(tujuan==='gain'){document.getElementById('metodeEnergi').value='30';pk.value='1.2';}
 else if(tujuan==='tktp'){document.getElementById('metodeEnergi').value='30';pk.value='1.2';}
 else if(tujuan==='elderly'){document.getElementById('metodeEnergi').value='25';pk.value='1.0';}
 else {document.getElementById('metodeEnergi').value='25';pk.value='1.0';}
 calculate();
}
function autoDiagnosis(){
 const o=document.getElementById('diagnosisOption').value;
 const bb=parseFloat(document.getElementById('bb').value);
 const status=document.getElementById('statusGizi').value;
 const nafsu=document.querySelector('[name="nafsu"]').value;
 const gastro=document.querySelector('[name="gastro"]').value;
 const recall=document.querySelector('[name="recall"]').value;
 let P='',E='',S='';
 const low=recall?'riwayat asupan makan yang tidak mencukupi kebutuhan':'asupan makan yang tidak mencukupi kebutuhan';
 if(o==='energy'){P='Asupan energi tidak adekuat';E=nafsu==='Menurun'?'berkaitan dengan penurunan nafsu makan': 'berkaitan dengan asupan makanan yang tidak mencukupi kebutuhan';S='ditandai dengan '+low+(nafsu==='Menurun'?' dan/atau nafsu makan menurun':'');}
 if(o==='protein'){P='Asupan protein tidak adekuat';E='berkaitan dengan asupan sumber protein yang tidak mencukupi kebutuhan';S='ditandai dengan asupan protein yang tidak mencukupi kebutuhan';}
 if(o==='excess'){P='Asupan energi berlebih';E='berkaitan dengan asupan energi yang melebihi kebutuhan';S='ditandai dengan pola makan/asupan energi berlebih';}
 if(o==='weightloss'){P='Penurunan berat badan tidak diharapkan';E='berkaitan dengan asupan energi yang tidak mencukupi kebutuhan';S='ditandai dengan adanya penurunan berat badan';}
 if(o==='overweight'){P='Kelebihan berat badan';E='berkaitan dengan ketidakseimbangan asupan energi dan pengeluaran energi';S='ditandai dengan IMT '+(status||'di atas rentang normal');}
 if(o==='knowledge'){P='Kurang pengetahuan terkait gizi';E='berkaitan dengan kurangnya informasi/edukasi gizi';S='ditandai dengan adanya kebutuhan edukasi gizi';}
 if(o==='fluid'){P='Asupan cairan tidak adekuat';E='berkaitan dengan asupan cairan yang tidak mencukupi';S='ditandai dengan asupan cairan kurang dari kebutuhan';}
 if(o==='fiber'){P='Asupan serat tidak adekuat';E='berkaitan dengan rendahnya konsumsi sayur, buah, dan sumber serat';S='ditandai dengan asupan serat yang kurang dari anjuran';}
 if(o==='intake'){P='Asupan oral tidak adekuat';E='berkaitan dengan '+(nafsu==='Menurun'?'penurunan nafsu makan':(gastro||'kondisi yang menghambat asupan oral'));S='ditandai dengan asupan oral yang tidak memenuhi kebutuhan';}
 if(o==='custom'){return;}
 document.getElementById('problem').value=P;
 document.getElementById('etiology').value=E;
 document.getElementById('signs').value=S;
 document.getElementById('pes').value=P&&E&&S?P+' '+E+' '+S+'.':'';
}
document.getElementById('bb').addEventListener('input',()=>{calculate(); if(document.getElementById('diagnosisOption').value)autoDiagnosis();});
document.getElementById('tb').addEventListener('input',calculate);
document.getElementById('bbu').addEventListener('input',calculate);
document.getElementById('proteinKg').addEventListener('input',calculate);

function autoIntervention(){
 const diet=document.getElementById('jenisDiet').value;
 const strategi=document.getElementById('strategiIntervensi').value;
 const tujuan=document.getElementById('tujuanIntervensi');
 const pres=document.getElementById('preskripsiIntervensi');
 const eduk=document.getElementById('edukasiIntervensi');
 const map={
 'Diet TKTP':['Meningkatkan asupan energi dan protein sesuai kebutuhan','Diet TKTP sesuai kebutuhan energi/protein yang telah dihitung. Porsi kecil dan sering bila toleransi rendah.','Pilih sumber protein berkualitas, makanan padat energi, dan pantau toleransi.'],
 'Diet Diabetes Melitus':['Mengontrol asupan karbohidrat dan membantu mencapai target glikemik','Distribusi karbohidrat teratur, batasi gula sederhana, sesuaikan energi dengan kebutuhan pasien.','Edukasi porsi, jadwal makan, pilihan karbohidrat, dan pembatasan minuman/makanan tinggi gula.'],
 'Diet Rendah Garam':['Mengurangi asupan natrium sesuai kebutuhan klinis','Batasi garam, makanan tinggi natrium, makanan olahan/instan; sesuaikan dengan kondisi pasien.','Edukasi membaca label pangan dan memilih makanan rendah natrium.'],
 'Diet Rendah Lemak':['Mengurangi asupan lemak total terutama lemak jenuh','Batasi gorengan, santan pekat, kulit/lemak hewani; pilih teknik masak rendah lemak.','Edukasi pemilihan jenis lemak dan teknik pengolahan makanan.'],
 'Diet Tinggi Protein':['Meningkatkan asupan protein untuk memenuhi kebutuhan','Tambahkan sumber protein pada makan utama/snack sesuai kebutuhan.','Edukasi pilihan protein hewani dan nabati serta pembagian protein sepanjang hari.'],
 'Diet Rendah Protein':['Menyesuaikan asupan protein dengan kondisi klinis','Jumlah protein disesuaikan kebutuhan individual dan kondisi medis.','Edukasi pemilihan porsi sumber protein sesuai preskripsi.'],
 'Diet Rendah Serat':['Mengurangi beban serat sesuai kondisi pasien','Batasi sementara makanan tinggi serat sesuai indikasi dan toleransi.','Edukasi pemilihan makanan rendah serat sesuai anjuran.'],
 'Diet Tinggi Serat':['Meningkatkan asupan serat secara bertahap','Tingkatkan sayur, buah, dan sumber serat sesuai toleransi serta kebutuhan cairan.','Edukasi sumber serat dan peningkatan bertahap.'],
 'Diet Lunak':['Memenuhi kebutuhan gizi dengan tekstur yang mudah ditoleransi','Berikan makanan bertekstur lunak sesuai toleransi pasien.','Edukasi pemilihan dan pengolahan makanan bertekstur lunak.'],
 'Diet Cair':['Memenuhi kebutuhan gizi melalui bentuk cair sesuai indikasi','Sesuaikan jenis dan jumlah cairan dengan kondisi klinis serta toleransi.','Edukasi jadwal dan jenis cairan sesuai preskripsi.']
 };
 if(map[diet]){tujuan.value=map[diet][0];pres.value=map[diet][1];eduk.value=map[diet][2];}
 else if(strategi){tujuan.value=strategi;pres.value='Sesuaikan jenis, jumlah, bentuk, dan frekuensi makanan dengan kebutuhan gizi serta kondisi klinis pasien.';eduk.value='Berikan edukasi sesuai masalah gizi, pilihan makanan, porsi, jadwal makan, dan kepatuhan diet.';}
}
function autoMonev(){
 const p=document.getElementById('parameterMonev').value;
 const t=document.getElementById('targetMonev').value;
 if(p||t) document.getElementById('tindakLanjut').value='Lanjutkan intervensi dan evaluasi parameter '+(p||'sesuai masalah gizi')+' terhadap target: '+(t||'target individual')+'. Sesuaikan intervensi bila target belum tercapai.';
}
function getData(){
 const data={};
 new FormData(form).forEach((v,k)=>data[k]=v);
 data.imt=document.getElementById('imtResult').textContent;
 return data;
}
function saveData(){
 localStorage.setItem('fmc_asuhan_gizi',JSON.stringify(getData()));
 alert('Data berhasil disimpan di browser perangkat ini.');
}
function loadData(){
 const data=JSON.parse(localStorage.getItem('fmc_asuhan_gizi')||'null');
 if(!data){alert('Belum ada data tersimpan.');return;}
 Object.entries(data).forEach(([k,v])=>{
   const el=form.elements[k];
   if(el) el.value=v;
 });
 calculate();
 alert('Data berhasil dimuat.');
}
function resetForm(){
 setTimeout(()=>{
   document.getElementById('tanggal').value=today;
   document.getElementById('tanggal_pengisian').value=today;
   calculate();
 },0);
}
calculate();
</script>
</body>
</html>
