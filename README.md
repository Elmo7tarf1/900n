
<html>
<title>The Wolf Host Auto Exploit</title>
<style>
html, body {
background-image: url("img/logo.png");
background-size: 100%;
background-repeat: no-repeat;
background-color: #24272b;
color: white;
text-align: center;
margin: 0px;
overflow: hidden;
}

h1 {
text-shadow: 0.1em 0.1em 0.2em black;
font-size: 25px;
text-align: center;
color: white;
}

.TextCaption{
display: block;
    font-size: 20px;
    color: #fff;
    text-decoration: none;
}

a img {
    display: inline-block;  text-decoration: none;
}
a {
    display: inline-block;  text-decoration: none;
}

a:hover {
  animation: shake 0.5s infinite;
}
@keyframes shake {
  0% { transform: translateX(0); }
  20% { transform: translateX(-5px); }
  40% { transform: translateX(5px); }
  60% { transform: translateX(-5px); }
  80% { transform: translateX(5px); }
  100% { transform: translateX(0); }
}
</style>
<script>
if (window.applicationCache.status=='0'){window.location.replace("cache.html");}

function pldone() {
  progress.innerHTML= LoadedMSG;
}

function awaitpl() {
  progress.innerHTML= "You can send now any payload over netcat port 9020";
}
function wk_keep_alive()
{
    var xhr = new XMLHttpRequest();
    xhr.open('GET', document.location.href, false);
    xhr.send('');
}
function print(){}

function getScript(source,callback){var gs=document.createElement('script');gs.src=source;gs.onload=callback;gs.async=false;document.body.appendChild(gs);}
function loadScript(name)
{
	getScript(name,function(){});
}

  function loadFile(fileName) {
    let xhr = new XMLHttpRequest();
    xhr.open("GET", fileName, false);
    xhr.overrideMimeType("text/plain; charset=x-user-defined");
    xhr.send();
    let array = Uint8Array.from(xhr.response, c => c.charCodeAt(0));
    if (fileName.endsWith(".bz2")) {
      try {
        PLS = bzip2.simple(bzip2.array(array));
      } catch(error) {
        alert(fileName + ": \"" + error + "\"\n");
        throw error;
      }
    }
    return array;
  }
  
function load_pocj() {
var payload_buffer = chain.syscall(477, 0, 0x300000, 7, 0x1002, -1, 0);
            var buf = new Uint8Array(1);
            var buf_addr = p.leakval(buf);
            var old_buf = p.read8(buf_addr.add32(16));
            var old_sz = p.read4(buf_addr.add32(24));
            p.write8(buf_addr.add32(16), payload_buffer);
            p.write4(buf_addr.add32(24), PLS.length);
            for(var i = 0; i < PLS.length; i++) buf[i] = PLS[i];
            p.write8(buf_addr.add32(16), old_buf);
            p.write4(buf_addr.add32(24), old_sz);
            var pthread = p.malloc(0x10);
            chain.call(libKernelBase.add32(OFFSET_lk_pthread_create), pthread, 0x0, payload_buffer, 0);
            allset();
}

function jbdone() {
window.progress.innerHTML="<font color=#05f238> Jailbreak Done";
localStorage.setItem('fanthreshold', tempC.value);
for(var i=50; i<=80; i=i+5){
    var select = document.getElementById("tempC");
    var option = document.createElement("OPTION");
	select.options.add(option);
	option.text = i;
	option.value = i;
}
tempC.value=60;
all.style.display = "block";
}

function allset() {
window.progress.innerHTML= LoadedMSG
}

function Binset() {
window.progress.innerHTML="Payload Loaded. Send payloads to port 9020";
alert("Payload Loaded. Send payloads to port 9020");
}

function Mset() {
window.progress.innerHTML="Payload Loaded. Send payloads to port 9021";
alert("Payload Loaded. Send payloads to port 9021");
}

function runScript(what)
{
    var xhr = new XMLHttpRequest();
    xhr.open('GET', what, false);
    xhr.send('');
    eval.call(window, xhr.responseText);
}

function print(){}

function load_poc2() {
var payload_buffer = chain.syscall(477, 0x0, 0x300000, 0x7, 0x1000, 0xFFFFFFFF, 0);
 var payload_loader = p.malloc32(0x1000);
 var BLDR = payload_loader.backing;
 BLDR[0]=0x56415741;BLDR[1]=0x83485541;BLDR[2]=0x894818EC;BLDR[3]=0xC748243C;BLDR[4]=0x10082444;BLDR[5]=0x483C2302;BLDR[6]=0x102444C7;BLDR[7]=0x00000000;BLDR[8]=0x000002BF;BLDR[9]=0x0001BE00;BLDR[10]=0xD2310000;BLDR[11]=0x00009CE8;BLDR[12]=0xC7894100;BLDR[13]=0x8D48C789;BLDR[14]=0xBA082474;BLDR[15]=0x00000010;BLDR[16]=0x000095E8;BLDR[17]=0xFF894400;BLDR[18]=0x000001BE;BLDR[19]=0x0095E800;BLDR[20]=0x89440000;BLDR[21]=0x31F631FF;BLDR[22]=0x0062E8D2;BLDR[23]=0x89410000;BLDR[24]=0x2C8B4CC6;BLDR[25]=0x45C64124;BLDR[26]=0x05EBC300;BLDR[27]=0x01499848;BLDR[28]=0xF78944C5;BLDR[29]=0xBAEE894C;BLDR[30]=0x00001000;BLDR[31]=0x000025E8;BLDR[32]=0x7FC08500;BLDR[33]=0xFF8944E7;BLDR[34]=0x000026E8;BLDR[35]=0xF7894400;BLDR[36]=0x00001EE8;BLDR[37]=0x2414FF00;BLDR[38]=0x18C48348;BLDR[39]=0x5E415D41;BLDR[40]=0x31485F41;BLDR[41]=0xC748C3C0;BLDR[42]=0x000003C0;BLDR[43]=0xCA894900;BLDR[44]=0x48C3050F;BLDR[45]=0x0006C0C7;BLDR[46]=0x89490000;BLDR[47]=0xC3050FCA;BLDR[48]=0x1EC0C748;BLDR[49]=0x49000000;BLDR[50]=0x050FCA89;BLDR[51]=0xC0C748C3;BLDR[52]=0x00000061;BLDR[53]=0x0FCA8949;BLDR[54]=0xC748C305;BLDR[55]=0x000068C0;BLDR[56]=0xCA894900;BLDR[57]=0x48C3050F;BLDR[58]=0x006AC0C7;BLDR[59]=0x89490000;BLDR[60]=0xC3050FCA;
 chain.syscall(74, payload_loader, 0x4000, (0x1 | 0x2 | 0x4));
 var pthread = p.malloc(0x10); {
  chain.fcall(window.syscalls[203], payload_buffer, 0x300000);
  chain.fcall(libKernelBase.add32(OFFSET_lk_pthread_create), pthread, 0x0, payload_loader, payload_buffer);
 }
 chain.run();
 sessionStorage.Paload="yes";
 setTimeout(load_pocl,2000);
}

function load_pocl() {
var payload_buffer = chain.syscall(477, 0, 0x300000, 7, 0x1002, -1, 0);
            var buf = new Uint8Array(1);
            var buf_addr = p.leakval(buf);
            var old_buf = p.read8(buf_addr.add32(16));
            var old_sz = p.read4(buf_addr.add32(24));
            p.write8(buf_addr.add32(16), payload_buffer);
            p.write4(buf_addr.add32(24), PLS.length);
            for(var i = 0; i < PLS.length; i++) buf[i] = PLS[i];
            p.write8(buf_addr.add32(16), old_buf);
            p.write4(buf_addr.add32(24), old_sz);
            var pthread = p.malloc(0x10);
            chain.call(libKernelBase.add32(OFFSET_lk_pthread_create), pthread, 0x0, payload_buffer, 0);
            setTimeout(load_pocB,2000);
}
function load_pocB(){
 var req = new XMLHttpRequest();
 req.responseType = "arraybuffer";
 req.open('GET', PLfile);
 req.send();
 req.onreadystatechange = function () {
  if (req.readyState == 4) {
   PLD = req.response;
   var payload_buffer = chain.syscall(477, 0, PLD.byteLength*4 , 7, 0x1002, -1, 0);
   var pl = p.array_from_address(payload_buffer, PLD.byteLength*4);
   var padding = new Uint8Array(4 - (req.response.byteLength % 4) % 4);
   var tmp = new Uint8Array(req.response.byteLength + padding.byteLength);
   tmp.set(new Uint8Array(req.response), 0);
   tmp.set(padding, req.response.byteLength);
   var shellcode = new Uint32Array(tmp.buffer);
   pl.set(shellcode,0);
   var pthread = p.malloc(0x10);
   chain.call(libKernelBase.add32(OFFSET_lk_pthread_create), pthread, 0x0, payload_buffer, 0);
   allset();
  }
 };
}

function load_Bloader(){
    progress.innerHTML="<h1 style='font-size:25px;text-align:center;'>Loading NetCat Bin Server Port 9020!!!</h1>";
    var payload_buffer = chain.syscall(477, 0x0, 0x300000, 0x7, 0x1000, 0xFFFFFFFF, 0);
    var payload_loader = p.malloc32(0x1000);
    var loader_writer = payload_loader.backing;
    loader_writer[0] = 0x56415741;
    loader_writer[1] = 0x83485541;
    loader_writer[2] = 0x894818EC;
    loader_writer[3] = 0xC748243C;
    loader_writer[4] = 0x10082444;
    loader_writer[5] = 0x483C2302;
    loader_writer[6] = 0x102444C7;
    loader_writer[7] = 0x00000000;
    loader_writer[8] = 0x000002BF;
    loader_writer[9] = 0x0001BE00;
    loader_writer[10] = 0xD2310000;
    loader_writer[11] = 0x00009CE8;
    loader_writer[12] = 0xC7894100;
    loader_writer[13] = 0x8D48C789;
    loader_writer[14] = 0xBA082474;
    loader_writer[15] = 0x00000010;
    loader_writer[16] = 0x000095E8;
    loader_writer[17] = 0xFF894400;
    loader_writer[18] = 0x000001BE;
    loader_writer[19] = 0x0095E800;
    loader_writer[20] = 0x89440000;
    loader_writer[21] = 0x31F631FF;
    loader_writer[22] = 0x0062E8D2;
    loader_writer[23] = 0x89410000;
    loader_writer[24] = 0x2C8B4CC6;
    loader_writer[25] = 0x45C64124;
    loader_writer[26] = 0x05EBC300;
    loader_writer[27] = 0x01499848;
    loader_writer[28] = 0xF78944C5;
    loader_writer[29] = 0xBAEE894C;
    loader_writer[30] = 0x00001000;
    loader_writer[31] = 0x000025E8;
    loader_writer[32] = 0x7FC08500;
    loader_writer[33] = 0xFF8944E7;
    loader_writer[34] = 0x000026E8;
    loader_writer[35] = 0xF7894400;
    loader_writer[36] = 0x00001EE8;
    loader_writer[37] = 0x2414FF00;
    loader_writer[38] = 0x18C48348;
    loader_writer[39] = 0x5E415D41;
    loader_writer[40] = 0x31485F41;
    loader_writer[41] = 0xC748C3C0;
    loader_writer[42] = 0x000003C0;
    loader_writer[43] = 0xCA894900;
    loader_writer[44] = 0x48C3050F;
    loader_writer[45] = 0x0006C0C7;
    loader_writer[46] = 0x89490000;
    loader_writer[47] = 0xC3050FCA;
    loader_writer[48] = 0x1EC0C748;
    loader_writer[49] = 0x49000000;
    loader_writer[50] = 0x050FCA89;
    loader_writer[51] = 0xC0C748C3;
    loader_writer[52] = 0x00000061;
    loader_writer[53] = 0x0FCA8949;
    loader_writer[54] = 0xC748C305;
    loader_writer[55] = 0x000068C0;
    loader_writer[56] = 0xCA894900;
    loader_writer[57] = 0x48C3050F;
    loader_writer[58] = 0x006AC0C7;
    loader_writer[59] = 0x89490000;
    loader_writer[60] = 0xC3050FCA;
    chain.syscall(74, payload_loader, 0x4000, (0x1 | 0x2 | 0x4));
    var pthread = p.malloc(0x10);
    //
    {
        chain.fcall(window.syscalls[203], payload_buffer, 0x300000);
        chain.fcall(libKernelBase.add32(OFFSET_lk_pthread_create), pthread, 0x0, payload_loader, payload_buffer);
    }
    chain.run();
    awaitpl();
}

function load_PSXITA1gb(){
progress.innerHTML="Linux Loader 1GB loading... please wait"; 
LoadedMSG="LinuxLoader 1GB Loaded";
PLfile = "./paylode/PSXITA1gb.bin";
var script = document.createElement('script');script.src = "./paylode/MiraLoader.js";document.getElementsByTagName('head')[0].appendChild(script);
if(sessionStorage.Payload!="yes"){setTimeout(load_poc2, 500);} else {load_pocB();}
}

function load_PSXITA2gb(){
progress.innerHTML="Linux Loader 2GB loading... please wait"; 
LoadedMSG="LinuxLoader 2GB Loaded";
PLfile = "./paylode/PSXITA2gb.bin";
var script = document.createElement('script');script.src = "./paylode/MiraLoader.js";document.getElementsByTagName('head')[0].appendChild(script);
if(sessionStorage.Payload!="yes"){setTimeout(load_poc2, 500);} else {load_pocB();}
}

function load_PSXITA3gb(){
progress.innerHTML="Linux Loader 3GB loading... please wait"; 
LoadedMSG="LinuxLoader 3GB Loaded";
PLfile = "./paylode/PSXITA3gb.bin";
var script = document.createElement('script');script.src = "./paylode/MiraLoader.js";document.getElementsByTagName('head')[0].appendChild(script);
if(sessionStorage.Payload!="yes"){setTimeout(load_poc2, 500);} else {load_pocB();}
}

function load_PSXITA4gb(){
progress.innerHTML="Linux Loader 4GB loading... please wait"; 
LoadedMSG="LinuxLoader 4GB Loaded";
PLfile = "./paylode/PSXITA4gb.bin";
var script = document.createElement('script');script.src = "./paylode/MiraLoader.js";document.getElementsByTagName('head')[0].appendChild(script);
if(sessionStorage.Payload!="yes"){setTimeout(load_poc2, 500);} else {load_pocB();}
}

function load_PSXITA5gb(){
progress.innerHTML="Linux Loader 5GB loading... please wait"; 
LoadedMSG="LinuxLoader 5GB Loaded";
PLfile = "./paylode/PSXITA5gb.bin";
var script = document.createElement('script');script.src = "./paylode/MiraLoader.js";document.getElementsByTagName('head')[0].appendChild(script);
if(sessionStorage.Payload!="yes"){setTimeout(load_poc2, 500);} else {load_pocB();}
}


function load_goldhenv24b16(){
    progress.innerHTML="GoldHEN v.2.4b16 loading... please wait";
    LoadedMSG="GoldHEN v.2.4b16 Loaded";
    PLfile = "./paylode/goldhenv24b16.bin";
    out_jb = "AllPL";
    load_pocB();
}

function load_enableupdate(){
    progress.innerHTML="Payload  (Enable Update)"; LoadedMSG="Loaded (Enable Update)";
    setTimeout(function(){ let array = loadFile('./paylode/enableupdate.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_disableupdate(){
    progress.innerHTML="Payload....(Disable Update)"; LoadedMSG="Loaded (Disable Update)";
    setTimeout(function(){ let array = loadFile('./paylode/disableupdates.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_App2usb(){
    progress.innerHTML="Payload....(App2usb)"; LoadedMSG="Loaded (App2usb)";
    setTimeout(function(){ let array = loadFile('./paylode/app2usb.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_Dumper(){
    progress.innerHTML="Payload....(Dumper)"; LoadedMSG="Loaded  (Dumper)";
    setTimeout(function(){ let array = loadFile('./paylode/dumper.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_HistoryBlocker(){
    progress.innerHTML="Payload....(History Blocker)"; LoadedMSG="Loaded (History Blocker)";
    setTimeout(function(){ let array = loadFile('./paylode/historyblocker.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_kerneldumper(){
    progress.innerHTML="Payload....(Kernel Dumper)"; LoadedMSG="Loaded (Kernel Dumper)";
    setTimeout(function(){ let array = loadFile('./paylode/kerneldumper.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_ps4debug(){
    progress.innerHTML="Payload....(Ps4 Debug)"; LoadedMSG="Loaded (Ps4 Debug)";
    setTimeout(function(){ let array = loadFile('./paylode/ps4debug.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_pkgbackup(){
    progress.innerHTML="Payload....(pkg backup)"; LoadedMSG="Loaded (pkg backup)";
    setTimeout(function(){ let array = loadFile('./paylode/pkgbackup.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_WebRTE(){
    progress.innerHTML="Payload....(WebRTE)"; LoadedMSG="Loaded (WebRTE)";
    setTimeout(function(){ let array = loadFile('./paylode/webrte.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_ArabicGuy100(){
    progress.innerHTML="Payload....(ArabicGuy Mod 1.00)"; LoadedMSG="Loaded (ArabicGuy Mod 1.00)";
    setTimeout(function(){ let array = loadFile('./paylode/arabicguy100.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_ArabicGuy127(){
    progress.innerHTML="Payload....(ArabicGuy Mod 1.27)"; LoadedMSG="Loaded (ArabicGuy Mod 1.27)";
    setTimeout(function(){ let array = loadFile('./paylode/arabicguy127.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_ArabicGuy132(){
    progress.innerHTML="Payload....(ArabicGuyMod 1.32)"; LoadedMSG="Loaded (ArabicGuyMod 1.32)";
    setTimeout(function(){ let array = loadFile('./paylode/arabicguy132.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_Beefqueef138(){
    progress.innerHTML="Payload....(Beef Queef Mod 1.38)"; LoadedMSG="Loaded (Beef Queef Mod 1.38)";
    setTimeout(function(){ let array = loadFile('./paylode/beefqueef138.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_Beefqueef147(){
    progress.innerHTML="Payload....(Beef Queef Mod 1.47)"; LoadedMSG="Loaded (Beef Queef Mod 1.47)";
    setTimeout(function(){ let array = loadFile('./paylode/beefqueef147.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_Lush138(){
    progress.innerHTML="Payload....(Expulsions Mod 1.38)"; LoadedMSG="Loaded (Expulsions Mod 1.38)";
    setTimeout(function(){ let array = loadFile('./paylode/Lush138.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_WildeModz132(){
    progress.innerHTML="Payload....(Wilde Modz Mod 1.32)"; LoadedMSG="Loaded (Wilde Modz Mod 1.32)";
    setTimeout(function(){ let array = loadFile('./paylode/WildeModz132.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}


function load_WildeModz138(){
    progress.innerHTML="Payload....(Wilde Modz 1.38)"; LoadedMSG="Loaded (Wilde Modz 1.38)";
    setTimeout(function(){ let array = loadFile('./paylode/WildeModz138.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_WildeModz147(){
    progress.innerHTML="Payload....(GTA Modz 1.47)"; LoadedMSG="Loaded (GTA Modz 1.47)";
    setTimeout(function(){ let array = loadFile('./paylode/WildeModz148.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_Lamance138(){
    progress.innerHTML="Payload....(Lamance 1.38)"; LoadedMSG="Loaded (Lamance 1.38)";
    setTimeout(function(){ let array = loadFile('./paylode/Lamance.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_modRDE2100(){
    progress.innerHTML="Payload....(Rd2 Mod 1.00)"; LoadedMSG="Loaded (Rd2 Mod 1.00)";
    setTimeout(function(){ let array = loadFile('./paylode/oystersmenu100.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_modRDE2113(){
    progress.innerHTML="Payload....(Rd2 Mod 1.13)"; LoadedMSG="Loaded (Rd2 Mod 1.13) ";
    setTimeout(function(){ let array = loadFile('./paylode/oystersmenu113.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_modRDE2119(){
    progress.innerHTML="Payload....(Rd2 Mod 1.19)"; LoadedMSG="Loaded (Rd2 Mod 1.19)";
    setTimeout(function(){ let array = loadFile('./paylode/oystersmenu119.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_modRDE2124(){
    progress.innerHTML="Payload....( Rd2 Mod 1.24)"; LoadedMSG="Loaded ( Rd2 Mod 1.24)";
    setTimeout(function(){ let array = loadFile('./paylode/oystersmenu124.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_modRDE2129(){
    progress.innerHTML="Payload....( Rd2 Mod 1.29)"; LoadedMSG="Loaded (Rd2 Mod 1.29)";
    setTimeout(function(){ let array = loadFile('./paylode/oystersmenu129.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_NorthBeta(){
    progress.innerHTML="Payload....( North Beta 1.29)"; LoadedMSG="Loaded (North Beta 1.29)";
    setTimeout(function(){ let array = loadFile('./paylode/NorthBeta011.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_fan(){
    progress.innerHTML="Payload....(FAN SPEED)"; LoadedMSG="Loaded (FAN SPEED)";
    let array = loadFile("./paylode/fan" +tempC.value+ ".bin.bz2");
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_CopyCH(){
    progress.innerHTML="Payload....(CopyCh)"; LoadedMSG="Loaded (Copych)";
    setTimeout(function(){ let array = loadFile('./paylode/Copych.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_temperature(){
    progress.innerHTML="Payload....(temperature ps4)"; LoadedMSG="Loaded (temperature ps4)";
    setTimeout(function(){ let array = loadFile('./paylode/temperature.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

function load_toolbox(){
    progress.innerHTML="Payload....(toolbox ps4)"; LoadedMSG="Loaded (toolbox ps4)";
    setTimeout(function(){ let array = loadFile('./paylode/toolbox.bin.bz2');}, 50);
    out_jb = "AllPL";     setTimeout(load_pocj, 500);
}

</script>

<script src="./int64.js"></script>
<script src="./rop.js"></script>
<script src="./kexploit.js"></script>
<script type=module src="./alert.mjs"></script>

</head>

<br><br><br><br>
<h1 id=progress style='font-size:25px;text-align:center;'>Jailbreaking <font color=#fc0404> ( Please wait ) ....</h1>
<div id=all style="text-align:center;display:none">
<href id="cnmuhide1"   onmouseover=" 
(document.getElementById('spoiler2') .style.display='none');
(document.getElementById('spoiler3') .style.display='none');
(document.getElementById('spoiler4') .style.display='none');
(document.getElementById('spoiler5') .style.display='none');
(document.getElementById('spoiler6') .style.display='none');
(document.getElementById('spoiler8') .style.display='none')
(document.getElementById('spoiler7') .style.display='none');"> 
</href><href id="cnmuhide2"  onmouseover="if(document.getElementById('spoiler2') .style.display=='none') 
{
(document.getElementById('spoiler2') .style.display='');
(document.getElementById('spoiler3') .style.display='none');
(document.getElementById('spoiler4') .style.display='none');
(document.getElementById('spoiler5') .style.display='none');
(document.getElementById('spoiler6') .style.display='none');
(document.getElementById('spoiler7') .style.display='none')
(document.getElementById('spoiler8') .style.display='none');}else{document.getElementById('spoiler2') .style.display='none'}"> 
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_goldhenv24b16()"onMouseOver="progress.innerHTML='GoldHen v.2.4.b16 By SiSTRO'"><img src="img/hen1.png"125"/></a>
</href><href id="cnmuhide4"  onmouseover="if(document.getElementById('spoiler3') .style.display=='none') 
{
(document.getElementById('spoiler2') .style.display='none');
(document.getElementById('spoiler3') .style.display='');
(document.getElementById('spoiler4') .style.display='none');
(document.getElementById('spoiler5') .style.display='none');
(document.getElementById('spoiler6') .style.display='none');
(document.getElementById('spoiler7') .style.display='none')
(document.getElementById('spoiler8') .style.display='none');}else{document.getElementById('spoiler3') .style.display='none'}"> 
&nbsp;&nbsp;&nbsp;<a href="#"onMouseOver="progress.innerHTML='Stop and activate the PlayStation 4 update'"><img src="img/updat.png"></a>
</href><href id="cnmuhide3"  onmouseover="if(document.getElementById('spoiler4') .style.display=='none') 
{
(document.getElementById('spoiler2') .style.display='none');
(document.getElementById('spoiler3') .style.display='none');
(document.getElementById('spoiler4') .style.display='');
(document.getElementById('spoiler5') .style.display='none');
(document.getElementById('spoiler6') .style.display='none');
(document.getElementById('spoiler7') .style.display='none')
(document.getElementById('spoiler8') .style.display='none');}else{document.getElementById('spoiler4') .style.display='none'}"> 
&nbsp;&nbsp;&nbsp;<a href="#"onMouseOver="progress.innerHTML='PlayStation 4 device tools'"><img src="img/tools.png"></a>
</href><href id="cnmuhide5"  onmouseover="if(document.getElementById('spoiler5') .style.display=='none') 
{
(document.getElementById('spoiler2') .style.display='none');
(document.getElementById('spoiler3') .style.display='none');
(document.getElementById('spoiler4') .style.display='none');
(document.getElementById('spoiler5') .style.display='');
(document.getElementById('spoiler6') .style.display='none');
(document.getElementById('spoiler7') .style.display='none')
(document.getElementById('spoiler8') .style.display='none');}else{document.getElementById('spoiler5') .style.display='none'}"> 
&nbsp;&nbsp;&nbsp;<a href="#"onMouseOver="progress.innerHTML='Run cheats for PlayStation 4 games'"><img src="img/trenar.png"></a>
</href><href id="cnmuhide6"  onmouseover="if(document.getElementById('spoiler6') .style.display=='none') 
{
(document.getElementById('spoiler2') .style.display='none');
(document.getElementById('spoiler3') .style.display='none');
(document.getElementById('spoiler4') .style.display='none');
(document.getElementById('spoiler5') .style.display='none');
(document.getElementById('spoiler6') .style.display='');
(document.getElementById('spoiler7') .style.display='none')
(document.getElementById('spoiler8') .style.display='none');}else{document.getElementById('spoiler6') .style.display='none'}"> 
&nbsp;&nbsp;&nbsp;<a href="#"onMouseOver="progress.innerHTML='Run Linux on the PlayStation 4'"><img src="img/links1.png"></a>
</href><href id="cnmuhide7"  onmouseover="if(document.getElementById('spoiler7') .style.display=='none') 
{
(document.getElementById('spoiler2') .style.display='none');
(document.getElementById('spoiler3') .style.display='none');
(document.getElementById('spoiler4') .style.display='none');
(document.getElementById('spoiler5') .style.display='none');
(document.getElementById('spoiler6') .style.display='none');
(document.getElementById('spoiler7') .style.display='');
(document.getElementById('spoiler8') .style.display='none');}else{document.getElementById('spoiler7') .style.display='none'}"> 
&nbsp;&nbsp;<a href="#"onMouseOver="progress.innerHTML='Play Red Dead Redemption 2 mods on PlayStation 4'"><img src="img/rd1.png"></a>
</href><href id="cnmuhide8"  onmouseover="if(document.getElementById('spoiler8') .style.display=='none') 
{
(document.getElementById('spoiler2') .style.display='none');
(document.getElementById('spoiler3') .style.display='none');
(document.getElementById('spoiler4') .style.display='none');
(document.getElementById('spoiler5') .style.display='none');
(document.getElementById('spoiler6') .style.display='none');
(document.getElementById('spoiler7') .style.display='none');
(document.getElementById('spoiler8') .style.display='');}else{document.getElementById('spoiler8') .style.display='none'}"> 
&nbsp;&nbsp;<a href="#"onMouseOver="progress.innerHTML='Play Grand Theft Auto V mods on PlayStation 4'"><img src="img/gta1.png"></a>
</href></center>
</br>
<div id="spoiler2" style="display:none"> <br>
</div>
<div id="spoiler3" style="display:none"> <br>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_enableupdate()"onMouseOver="progress.innerHTML='Enable-Updates v1.0 - By Al Azif'"><img src="img/Enable.png "><span class="TextCaption">Enable</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_disableupdate()"onMouseOver="progress.innerHTML='Disable-Updates v1.0 - By Al Azif'"><img src="img/Disable.png"><span class="TextCaption">Disable</span></a>
</div>
<div id="spoiler4" style="display:none">
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_App2usb()"onMouseOver="progress.innerHTML='Move installed games to an external USB drive- By Al Azif'"><img src="img/AppToUsb.png"><span class="TextCaption">App2usb</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_Dumper()"onMouseOver="progress.innerHTML='It Is The Process Pf Copying CD PS4 And Putting It On USB- By Al Azif'"><img src="img/Dumper.png"><span class="TextCaption">Dumper</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_pkgbackup()"onMouseOver="progress.innerHTML='progress.innerHTML='This is a pkg backup for usb- By Al Azif'"><img src="img/pkgbackup.png"><span class="TextCaption">PKG Backup</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_HistoryBlocker()" onMouseOver="progress.innerHTML='Run history blocker on PS4- By Al Azif'"><img src="img/HistoryBlocker.png"><span class="TextCaption">History Blocker</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_temperature()" onMouseOver="progress.innerHTML='payload gives you notification of how hot your PlayStation 4 is'"><img src="img/temperature.png"125"/><span class="TextCaption">temperature</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_toolbox()"onMouseOver="progress.innerHTML='progress.innerHTML='This is a TOOL BOX for usb- By Al Azif'"><img src="img/toolbox.png"><span class="TextCaption">TOOL BOX</span></a>
<br>
&nbsp;&nbsp;&nbsp;<a href="https://pkg-zone.com/install" onMouseOver="progress.innerHTML='You can now install the Homebrew Store using only the PKG-Zone website through the Browser!'"><img src="img/hb.png"><span class="TextCaption"> install HB Store</span></a>
&nbsp;&nbsp;&nbsp;<a href="paylode/webactivate.html" onMouseOver="progress.innerHTML='This is a debugger for PlayStation 4 and a save transfer for games without a PC without PC'"><img src="img/ps4debug.png"125"/><span class="TextCaption">Web-Activator</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_ps4debug()" onMouseOver="progress.innerHTML='This is a debugger for PlayStation 4 and a save transfer for gameswithout PC- By Al Azif'"><img src="img/Web-Activator.png"><span class="TextCaption">Ps4debug</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_Bloader()"onMouseOver="progress.innerHTML='Loads a bin file sent to the PS4 IP address on port 9021'"><img src="img/binloader.png"><span class="TextCaption">Bin Loader</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_kerneldumper()" onMouseOver="progress.innerHTML='Changes the internal clock of the PS4- By Al Azif'"><img src="img/KernelDumper.png"><span class="TextCaption">Kernel Dumper</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_fan()"onMouseOver="progress.innerHTML='FAN SPEED'"><img src="img/fanspeed.png"><span class="TextCaption"> FAN SPEED </span></a><select id="tempC"></select>&#176;C</a>
</div>
<div id="spoiler5" style="display:none">
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_WebRTE()"onMouseOver="progress.innerHTML='WebRTE v1.0 on PS4- By Karo'"><img src="img/WebRTE.png"><span class="TextCaption">WebRTE</span></a>
&nbsp;&nbsp;&nbsp;<a href="http://wolf2022.ir/trainer/index.html"onMouseOver="progress.innerHTML='PS4 TRAINER Offline'"><img src="img/urtrainer.png"><span class="TextCaption">PS4 Trainer</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_CopyCH()"onMouseOver="progress.innerHTML='New Payload for copy json and shn files from USB to PS4 GoldHen path By-Karo'"><img src="img/CopyCH.png"><span class="TextCaption">Copy ( json OR Shn ) USB</span></a>
</div>
<div id="spoiler6" style="display:none">
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_PSXITA1gb()" onMouseOver="progress.innerHTML='Linux Vram Loader 1GB For Pro Consoles - 9.00 Port By PSXita'"><img src="img/links2.png"><span class="TextCaption">Linux Psxiat 1GB</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_PSXITA2gb()" onMouseOver="progress.innerHTML='Linux Vram Loader 2GB For Pro Consoles - 9.00 Port By PSXita '"><img src="img/links2.png"><span class="TextCaption">Linux Psxiat 2GB</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_PSXITA3gb()" onMouseOver="progress.innerHTML='Linux Vram Loader 3GB For Pro Consoles - 9.00 Port By PSXita '"><img src="img/links2.png"><span class="TextCaption">Linux Psxiat 3GB</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_PSXITA4gb()" onMouseOver="progress.innerHTML='Linux Vram Loader 4GB For Pro Consoles - 9.00 Port By PSXita '"><img src="img/links2.png"><span class="TextCaption">Linux Psxiat 4GB</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_PSXITA5gb()" onMouseOver="progress.innerHTML='Linux Vram Loader 5GB For Pro Consoles - 9.00 Port By PSXita '"><img src="img/links2.png"><span class="TextCaption">Linux Psxiat 5GB</span></a>
</div>
<div id="spoiler7" style="display:none"><br>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_modRDE2100()"onMouseOver="progress.innerHTML='Red Dead Redemption II Oysters Mod v1.3.8 For Update v1.00 -  By RF0oDxM0Dz'"><img src="img/rd2.png"><span class="TextCaption">Red Dead 1.00</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_modRDE2113()" onMouseOver="progress.innerHTML='Red Dead Redemption II Oysters Mod v1.3.8 For Update v1.13 -  By RF0oDxM0Dz'"><img src="img/rd2.png"><span class="TextCaption">Red Dead 1.13</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_modRDE2119()" onMouseOver="progress.innerHTML='Red Dead Redemption II Oysters Mod v1.3.8 For Update v1.19 -  By RF0oDxM0Dz'"><img src="img/rd2.png"><span class="TextCaption">Red Dead 1.19</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_modRDE2124()" onMouseOver="progress.innerHTML='Red Dead Redemption II Oysters Mod v1.3.8 For Update v1.24 -  By RF0oDxM0Dz'"><img src="img/rd2.png"><span class="TextCaption">Red Dead 1.24</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_modRDE2129()" onMouseOver="progress.innerHTML='Red Dead Redemption II Oysters Mod v1.3.8 For Update v1.29 -  By RF0oDxM0Dz'"><img src="img/rd2.png"><span class="TextCaption">Red Dead 1.29</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_NorthBeta()" onMouseOver="progress.innerHTML='Red Dead Redemption II North Beta Mod v0.11 For Update v1.29 - By David133Hax'"><img src="img/rd2.png"><span class="TextCaption">North Beta 1.29</span></a>

</div>
<div id="spoiler8" style="display:none">
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_ArabicGuy100()" onMouseOver="progress.innerHTML='ArabicGuy For GTA V Update v1.00 - By RF0oDxM0Dz'"><img src="img/gta2.png"><span class="TextCaption">ArabicGuy 1.00</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_ArabicGuy127()" onMouseOver="progress.innerHTML='ArabicGuy For GTA V Update v1.27 - By RF0oDxM0Dz'"><img src="img/gta2.png"><span class="TextCaption">ArabicGuy 1.27</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_ArabicGuy132()" onMouseOver="progress.innerHTML='ArabicGuy For GTA V Update v1.38 - By RF0oDxM0Dz'"><img src="img/gta2.png"><span class="TextCaption">ArabicGuy 1.32</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_Beefqueef138()"onMouseOver="progress.innerHTML='BeefQueefMod For GTA V Update v1.38 - By GraFfiX'"><img src="img/gta2.png"><span class="TextCaption">Beef Queef 1.38</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_Beefqueef147()"onMouseOver="progress.innerHTML='BeefQueefMod For GTA V Update v1.47 - By GraFfiX'"><img src="img/gta2.png"><span class="TextCaption">Beef Queef 1.47</span></a>
<BR>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_Lamance138()"onMouseOver="progress.innerHTML='Lamance v0.9 For GTA V Update v1.38 - By David133Hax'"><img src="img/gta2.png"><span class="TextCaption">Lamance 1.38</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_Lush138()"onMouseOver="progress.innerHTML='Expulsion Mod Menu v4.0 For GTA V Update v1.38 - By LushModz'"><img src="img/gta2.png"><span class="TextCaption">Expulsions 1.38</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_WildeModz132()"onMouseOver="progress.innerHTML='WildeModz v1.2 For GTA V Update v1.32 - By Wilde Modz'"><img src="img/gta2.png"><span class="TextCaption">Wilde Modz 1.32</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_WildeModz138()"onMouseOver="progress.innerHTML='WildeModz v1.7 For GTA V Update v1.38 - By Wilde Modz'"><img src="img/gta2.png"><span class="TextCaption">Wilde Modz 1.38</span></a>
&nbsp;&nbsp;&nbsp;<a href="#" onclick="load_WildeModz147()"onMouseOver="progress.innerHTML='GTA Modz v1.7 For GTA V Update v1.47 - By Wilde Modz'"><img src="img/gta2.png"><span class="TextCaption">Wilde Modz 1.47</span></a>
</div>
<a  style="margin-top: 240px;">
<h1 style="margin-top: 15px; color: red;">Special Thanks to:<a href="https://twitter.com/sleirsgoevy" style="color:white; margin-left: 15px;">@sleirsgoevy</a><a style="color:white; margin-left: 15px;">ChendoChap</a><a href="https://twitter.com/SpecterDev" style="color:white; margin-left: 15px;">@SpecterDev</a><a style="color:white; margin-left: 15px;">SiSTR0</a><a href="https://twitter.com/Znullptr" style="color:white; margin-left: 15px;">@Znullptr</a><a style="color:white; margin-left: 15px;">All developers who contributed to the ps4 scene ...</a></h1>
</div>
<script>
var bzip2 = {};

bzip2.array = function(bytes) {
  var bit = 0, byte = 0;
  var BITMASK = [0, 0x01, 0x03, 0x07, 0x0F, 0x1F, 0x3F, 0x7F, 0xFF];
  return function(n) {
    var result = 0;
    while (n > 0) {
      var left = 8 - bit;
      if (n >= left) {
        result <<= left;
        result |= (BITMASK[left] & bytes[byte++]);
        bit = 0;
        n -= left;
      } else {
        result <<= n;
        result |= ((bytes[byte] & (BITMASK[n] << (8 - n - bit))) >> (8 - n - bit));
        bit += n;
        n = 0;
      }
    }
    return result;
  }
};

bzip2.simple = function(bits) {
  var size = bzip2.header(bits);
  var all = [], chunk = [];
  do {
    all = all.concat(chunk);
    chunk = bzip2.decompress(bits, size);
  } while (chunk != -1);
  return Uint8Array.from(all);
};

bzip2.header = function(bits) {
  if (bits(8 * 3) != 4348520) throw "No magic number found.";
  var i = bits(8) - 48;
  if (i < 1 || i > 9) throw "Not a bzip2 archive.";
  return i;
};

// Param1: a function for reading the block data (starting with 0x314159265359)
// Param2: block size (0-9) (optional, defaults to 9)
// Param3: length at which to stop decompressing and return the output
bzip2.decompress = function(bits, size, len) {
  var MAX_HUFCODE_BITS = 20;
  var MAX_SYMBOLS = 258;
  var SYMBOL_RUNA = 0;
  var SYMBOL_RUNB = 1;
  var GROUP_SIZE = 50;

  var bufsize = 100000 * size;
  for (var h = "", i = 0; i < 6; i++) h += bits(8).toString(16);
  if (h == "177245385090") return -1; // Last block
  if (h != "314159265359") throw "Not valid bzip2 data.";
  bits(32); // Ignore CRC codes
  if (bits(1)) throw "Unsupported obsolete version.";
  var origPtr = bits(24);
  if(origPtr > bufsize) throw "Initial position larger than buffer size.";
  var t = bits(16);
  var symToByte = new Uint8Array(256),
      symTotal = 0;
  for (i = 0; i < 16; i++) {
    if (t & (1 << (15 - i))) {
      var k = bits(16);
      for (j = 0; j < 16; j++) {
        if (k & (1 << (15 - j))) {
          symToByte[symTotal++] = (16 * i) + j;
        }
      }
    }
  }

  var groupCount = bits(3);
  if (groupCount < 2 || groupCount > 6) throw "Error 1 while decompressing.";
  var nSelectors = bits(15);
  if (nSelectors == 0) throw "Error 2 while decompressing.";
  var mtfSymbol = []; // TODO: possibly replace JS array with typed arrays
  for (var i = 0; i < groupCount; i++) mtfSymbol[i] = i;
  var selectors = new Uint8Array(32768);

  for (var i = 0; i < nSelectors; i++) {
    for (var j = 0; bits(1); j++) if (j >= groupCount) throw "Error 3 while decompressing.";
    var uc = mtfSymbol[j];
    mtfSymbol.splice(j, 1); // This is a probably inefficient MTF transform
    mtfSymbol.splice(0, 0, uc);
    selectors[i] = uc;
  }

  var symCount = symTotal + 2;
  var groups = [];
  for (var j = 0; j < groupCount; j++) {
    var length = new Uint8Array(MAX_SYMBOLS),
        temp = new Uint8Array(MAX_HUFCODE_BITS + 1);
    t = bits(5); // Lengths
    for (var i = 0; i < symCount; i++) {
      while (true) {
        if (t < 1 || t > MAX_HUFCODE_BITS) throw "Error 4 while decompressing.";
        if (!bits(1)) break;
        if (!bits(1)) t++;
        else t--;
      }
      length[i] = t;
    }
    var  minLen,  maxLen;
    minLen = maxLen = length[0];
    for (var i = 1; i < symCount; i++) {
      if (length[i] > maxLen) maxLen = length[i];
      else if (length[i] < minLen) minLen = length[i];
    }
    var hufGroup;
    hufGroup = groups[j] = {};
    hufGroup.permute = new Uint32Array(MAX_SYMBOLS);
    hufGroup.limit = new Uint32Array(MAX_HUFCODE_BITS + 1);
    hufGroup.base = new Uint32Array(MAX_HUFCODE_BITS + 1);
    hufGroup.minLen = minLen;
    hufGroup.maxLen = maxLen;
    var base = hufGroup.base.subarray(1);
    var limit = hufGroup.limit.subarray(1);
    var pp = 0;
    for (var i = minLen; i <= maxLen; i++)
      for (var t = 0; t < symCount; t++)
      if (length[t] == i) hufGroup.permute[pp++] = t;
      for (i = minLen; i <= maxLen; i++) temp[i] = limit[i] = 0;
      for (i = 0; i < symCount; i++) temp[length[i]]++;
      pp = t = 0;
      for (i = minLen; i < maxLen; i++) {
        pp += temp[i];
        limit[i] = pp - 1;
        pp <<= 1;
        base[i + 1] = pp - (t += temp[i]);
      }
      limit[maxLen] = pp + temp[maxLen] - 1;
      base[minLen] = 0;
  }
  var byteCount = new Uint32Array(256);
  for (var i = 0; i < 256; i++) mtfSymbol[i] = i;
  var runPos, count, symCount, selector;
  runPos = count = symCount = selector = 0;
  var buf = new Uint32Array(bufsize);
  while (true) {
    if (!(symCount--)) {
      symCount = GROUP_SIZE - 1;
      if (selector >= nSelectors) throw "Error 5 while decompressing.";
      hufGroup = groups[selectors[selector++]];
      base = hufGroup.base.subarray(1);
      limit = hufGroup.limit.subarray(1);
    }
    i = hufGroup.minLen;
    j = bits(i);
    while (true) {
      if (i > hufGroup.maxLen) throw "Error 6 while decompressing.";
      if (j <= limit[i]) break;
      i++;
      j = (j << 1) | bits(1);
    }
    j -= base[i];
    if (j < 0 || j >= MAX_SYMBOLS) throw "Error 7 while decompressing.";
    var nextSym = hufGroup.permute[j];
    if (nextSym == SYMBOL_RUNA || nextSym == SYMBOL_RUNB) {
      if (!runPos) {
        runPos = 1;
        t = 0;
      }
      if (nextSym == SYMBOL_RUNA) t += runPos;
      else t += 2 * runPos;
      runPos <<= 1;
      continue;
    }
    if (runPos) {
      runPos = 0;
      if (count + t >= bufsize) throw "Error 8 while decompressing.";
      uc = symToByte[mtfSymbol[0]];
      byteCount[uc] += t;
      while (t--) buf[count++] = uc;
    }
    if (nextSym > symTotal) break;
    if (count >= bufsize) throw "Error 9 while decompressing.";
    i = nextSym -1;
    uc = mtfSymbol[i];
    mtfSymbol.splice(i, 1);
    mtfSymbol.splice(0, 0, uc);
    uc = symToByte[uc];
    byteCount[uc]++;
    buf[count++] = uc;
  }
  if (origPtr < 0 || origPtr >= count) throw "Error 10 while decompressing.";
  var j = 0;
  for (var i = 0; i < 256; i++) {
    k = j + byteCount[i];
    byteCount[i] = j;
    j = k;
  }
  for (var i = 0; i < count; i++) {
    uc = buf[i] & 0xff;
    buf[byteCount[uc]] |= (i << 8);
    byteCount[uc]++;
  }
  var pos = 0, current = 0, run = 0;
  if (count) {
    pos = buf[origPtr];
    current = (pos & 0xff);
    pos >>= 8;
    run = -1;
  }
  count = count;
  var output = [];
  var copies, previous, outbyte;
  if (!len) len = Infinity;
  while (count) {
    count--;
    previous = current;
    pos = buf[pos];
    current = pos & 0xff;
    pos >>= 8;
    if (run++ == 3) {
      copies = current;
      outbyte = previous;
      current = -1;
    } else {
      copies = 1;
      outbyte = current;
    }
    while (copies--) {
      output.push(outbyte);
      if (!--len) return output;
    }
    if (current != previous) run = 0;
  }
  return output;
};
</script>
</body>
</html>
