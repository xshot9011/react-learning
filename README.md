# React

Created: Nov 6, 2020 7:23 PM
Tags: react
is_finished: No

# React Key Concepts

ทำไม React ถึงยังมีคนใช้อยู่ ปัญหาแบบไหนที่ react แก้ principle ที่เราควรเข้าใจ เราควรเข้าใจก่อนเราจะไปใช้ framework ใดๆก็ตาม

## The Birth of React

เมื่อก่อนเราก็มี html, css, js js ก็ทำหน้าที่จัดการงานต่างๆที่หน้าบ้าน แต่ปัญหามันเกิดขึ้นจากที่ website เนี่ยมันถูกรันได้บนหลายๆ browser ด้วยกันและแต่ละ browser ก็แตกต่างกันไปอีกเนื่องจากผู้พัฒนาเป็นคนละคน เราก็ต้องไปสร้าง js ให้ได้กับทุกๆ browser 

ต่อไปก็มีสิ่งที่เราเรียกว่า jQuery เกิดขึ้นทำให้เราสามารถทำงานร่วมกับ DOM ได้ง่าย DOM เนี่ยเป็นตัวกำหนดโครงสร้างเพจ ตอนที่เรากด f12 ดูอะ สิ่งที่ js ทำก็คือการ modify DOM

jQuery กำหนด syntax ขึ้นมาที่ทำให้ code เราสามารถรันได้บนทุก browser

dev ก็เริ่มทำแอพที่ใหญ่ขึ้นเรื่อยๆ ตามความสามารถของเทคโนโลยี

แล้วก็เกิดสิ่งที่เราเรียกว่า single page application ที่ไม่ต้องโหลดหน้า html ทุกรอบ → AJAX ตามมา ทำให้ web brwoser ทำงานได้เหมือน application มากขึ้น

augular → dev เริ่มทำ app ที่ซับซ้อนขึ้น → เมื่อ app ใหญ่ขึ้นแน่นอน bug นั้นก็ตามหายากขึ้น → code จำนวนมาก → จัดการยาก → facebook ก็เลยสร้าง react ขึ้นมาแทน เกิดจากการ mo โค็ดของ gg ใหม่หมดก้อน

## Declarative vs Imperative

Success of React come to 4 things

1. Don't touch the DOM. I'll do it

    DOM คือ Document Object Model มันคือสิ่งที่ browser ใช้ในการแสดง web site ของเรา และ javascript ก็มาจัดการ DOM เหล่านี้ แล้ว DOM พวกนี้ก็มี API ที่ใช้ในการเข้าถึงพวกมันอยู่เช่น document.getElementById(id) หรืออะไรก็ตามที่เราคุ้นชิน

    สิ่งที่เราทำให้เกิดการเปลี่ยนแปลงตามส่วนต่างๆของ website นั้นก็คือสิ่งที่เรียกว่า "imperative" ลอคอินปุ้ปไปเปลี่ยนหน้า เปลี่ยนนู้นแสดงผลชื่อ ทีละส่วน

    การจัดการ dom เนี่ยเป็นส่วนหนึ่งที่ทำให้เกิด performance bottlenecks มันใช้เวลาทำให้ dom เปลี่ยนแปลงนานมาก เช่นการ repaint (เปลี่ยน element และเพิ่มเข้าไปใน page) ต่อไปก็ refloat (การคำนวณ layout ใหม่)

    react ก็เลยบอกว่าการเปลี่ยน dom เนี่ยมันยากใช่ป่ะ บอกเราสิเดี่ยวเราจัดการหาวิธีในการเปลี่ยน DOM ที่ดีที่สุดให้ แค่บอกมาว่าหน้า app ของคุณเป็นยังไง

    เรามี js เป็น blueprint ที่คอยบอก react ว่าหน้าตา app เราจะเป็นยังไง เราไม่ต้องจัดการ dom เลย

    ![React%2064bca7ca33ea46faa22af98d1c892a74/Untitled.png](React%2064bca7ca33ea46faa22af98d1c892a74/Untitled.png)

    เราไม่ต้องไปกำหนด if นี่เปลี่ยนให้ไปเปลี่ยนอันนู้นอันนีอันนั้น

    แค่บอกว่าโครงสร้างเป็นยังไงเดี่ยว react ต่อมันเองเมื่อมีการเปลี่ยนแปลงใดๆ

## Component Architecture

2. Build website like LEGO blocks

react ถูกทำมาแบบ re-usable component แล้วคอมโพเน้นคืออะไร ก็พวกตัวอักษร สี ทั้งหมดเลย

react มีการรวม small componen เข้าด้วยกันทำให้เกิด big commonent เช่น profile component ที่มี component อันอื่นคลุมอยู่อีกอัน

เราสามารถเอา component หนึ่งไปไว้ที่ไหนก็ได้ ย้ายโปรเจ็ค หรือ ย้ายที่ในเจ็คเดียวกันก็ทำได้

component เนี่ยก็เป็น js ชุดหนึ่งที่รับ input แล้วแสดงผล โดยหลักการประมาณนี้

ไปที่ dev tool ใน browser เลื่อนไปที่ react จะเห็น component ทั้งหมด

## One Way Data Flow

3. Unidirectional data flow

react เป็น lib js ที่ทำให้เขียน js ได้มากขึ้น

เรามี state (javascript object), component ทำงานร่วมกันใน react lib 

สิ่งที่ react ทำคือการสร้าง virtualDOM ที่เราทำการติดตั้ง plugin เข้าไปแล้วดูที่ F12 อะ

VIRtualDom ทำให้ react รู้ว่าควรอัพเดทอะไรแล้วก็ทำงานโดยเหมือน 
function React (state, component) { ... }
ก็จะสร้าง DOM จริงๆออกมา แล้วเวลามีการอัพเดทแก้ไขหรือสร้าง react ก็จะไปดู blueprint (virtualDOM) แล้วก็ modify DOM 
ทุกครั้งที่เราอยากให้ web page ของเราเปลี่ยนไป state ก็ต้องเปลี่ยน เช่นเมื่อมีการ click เมาส์ลงไปที่ DOM สัก node หนึ่ง react ก็จะมาบอกว่า hey มีคนมาทำอะไรที่ node นี้นะแล้วเราจะทำอย่างไร (ที่เราเขียนเอง) → เกิด (การเปลี่ยน state)  state has been changed → then react (v) to the change → func (new state, com) → update the DOM 

ถ้าเกิดการเปลี่ยนแปลงของ state → virtual dom จะทำการส่ง data ลงไปยัง node ต่างๆข่างล่าง (ด้านล่างอย่างเดียว) เช่น if state is login node node นี้จะแสดงนะอันนี้ไม่แสดงนะ

debug ง่ายมากถ้าอันนั้น bug ไปที่ state นั้นแล้วดู node ที่อยู่ด้านล่างอย่างเดียวทำให้ง่ายต่อการดู

## UI Library

4. UI The rest is up to you

ถ้าเป็น framework มันมีทุกอย่างที่เราต้องการให้ แต่ react คือ lib ที่ทำให้เราสามารถจัดการกับ component only ที่เหลือเราไปหามาโมเอง

react ก็มีหลายตัวที่จัดการ บนคอมก็อีกตัว บนโทรศัพท์ก็อีกตัว (react native) บน cmd บน vr 

ตัวจัดการที่เราจะยึ่งอยู่ก็มี 2 แบบนั้นก็คือ react core, react dom robot ที่ช่วยเราจัดการ

## More on

ตอนนี้มี lib มากมายเกิดมาเน่ืองจาก react ให้เรามาแค่นั้น ที่เหลือเราต้องจัดการเองนั้นแหละทำไม lib เกิดมาเยอะ

สิ่งที่เรา react dev ทำ

1. decide on component
2. decide state and where it lives (virtual DOM)
3. what changes when state changes

[https://reactdesktop.js.org/](https://reactdesktop.js.org/)

[https://facebook.github.io/react-360/](https://facebook.github.io/react-360/)

[https://github.com/Yomguithereal/react-blessed](https://github.com/Yomguithereal/react-blessed)