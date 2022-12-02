# DADS5001_MiniProject_6420422011
ภาพรวมการให้บริการที่จอดรถของหน่วยงาน Singapore Housing & Development Board : มีการให้บริการอย่างไร และเมื่อดูจาก Factor ต่างๆ มีจุดไหนที่สามารถพัฒนาได้หรือไม่?



# Overview : What's HDB?

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/hdbsite-logo.jpg)

HDB หรือ Housing & Development Board คือองค์กรหนึ่งของประเทศสิงคโปร์ที่ดูแลจัดการเกี่ยวกับที่อยู่อาศัย ซึ่งมีหน้าที่เป็นผู้วางแผนและพัฒนาที่อยู่อาศัยและปรับปรุงเปลี่ยนแปลงเมืองสิงคโปร์เพื่อให้ประชาชนทุกคนที่อยู่ในสิงคโปร์มีคุณภาพชีวิตที่ดี HDB สร้างย่านการค้าหลายรูปแบบ สถานที่พักผ่อนทำกิจกรรมนันทนาการ และสร้าง facility ในเมืองให้ประชาชนอยู่อาศัยอย่างสะดวกสบาย
ซึ่งในที่นี่เราจะมาสรุปภาพรวมของ 1 ใน Facility ของ HDB นั่นก็คือ การให้บริการที่จอดรถ ว่าเป็นอย่างไรดังรายละเอียดด้านล่างค่ะ :)

Credit : 
https://propholic.com/prop-globe/%E0%B9%80%E0%B8%A2%E0%B8%B5%E0%B9%88%E0%B8%A2%E0%B8%A1%E0%B8%8A%E0%B8%A1-hdb-hub-%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%80%E0%B8%84%E0%B8%AB%E0%B8%B0%E0%B8%AA%E0%B8%B4%E0%B8%87%E0%B8%84%E0%B9%82%E0%B8%9B/

# Dataset
#### 1. Dataset ข้อมูลรายละเอียดจุดบริการที่จอดรถทั้งหมด (ข้อมูลอัพเดท ณ ก.ย. 2022)

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/source%20table3.JPG)
![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/source%20table1.JPG)

Source : https://data.gov.sg/dataset/hdb-carpark-information?view_id=398e65ae-e2cb-4312-8651-6e65d6f19ed1&resource_id=139a3035-e624-4f56-b63f-89ae28d4ae4c
- 2182 rows 
- 12 Columns : 
car_park_no, address, x_coord, y_coord, car_park_type, type_of_parking_system, short_term_parking, free_parking, night_parking, car_park_decks, gantry_height, car_park_basement

#### 2. Dataset Planning Areas of Singapore

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/source%20table4.JPG)


Source : https://en.wikipedia.org/wiki/Planning_Areas_of_Singapore
- 55 rows 
- 9 Columns : 
Name (English) , Malay, Chinese, Pinyin, Tamil, Region, Area (km²), Population[7], Density (/km²)

# How to create
#### 1. Load dataset & Cleansing : จากข้อมูล Datasetแรกพบว่าข้อมูลที่อยู่ค่อนข้างเป็น Freetext จึงต้องทำการ Cleansing ข้อมูลที่อยู่ เพื่อนำไปเชื่อมกับข้อมูล Region ใน Datasetที่ 2

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/cleansing.JPG)

#### 2. Merging Dataset : หลังจากทำการ Merging ข้อมูล จะพบกว่าข้อมูลรายละเอียดของที่จอดรถมีข้อมูล Region เพิ่มเติม ซึ่งทำให้สามารถจัดกลุ่มข้อมูลตามภูมิภาคเพื่อประกอบการวิเคราะห์เทียบกับ Factor อื่นๆ

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/merging%20dataset.JPG)

#### 3. Pivot & Visualization : นำข้อมูลจากข้อ 2 มา Pivot ในแง่มุมต่างๆ & Visualize ตามตัวอย่างด้านล่าง และ ในหัวข้อถัดไปค่ะ

![image](https://user-images.githubusercontent.com/115800837/196230255-b52f6e00-7a29-408d-a84d-da2dc3dcb904.png)

รายละเอียด code ทั้งหมด : https://github.com/Juntanep/DADS5001_MiniProject/blob/main/Mini%20project_HBD%20Carparking%20SG%20(Final).ipynb
# Question & Answer

จากจำนวนที่จอดรถทั้งหมด 2,182 แห่ง สามารถสรุปข้อมูลได้ ดังนี้

#### 1. Q: การกระจายตัวของที่จอดรถในแต่ละภูมิภาคเป็นอย่างไร?

![image](https://user-images.githubusercontent.com/115800837/196228837-e03034db-dda6-46ae-a183-7e1928c80a6e.png)

A: จากกราฟข้อมูล Number of Car Park by Region and Payment System จะพบว่า Overall HDB จะมีการให้บริการทั่วทุกภูมิภาคมากกว่า 2,000 จุด โดยกว่า 90% เป็นการให้บริการแบบ Electronic System โดยมีการใช้ Coupon System เพียงเล็กน้อยเท่านั้น 10%


ซึ่งเมื่อแยกออกมาแต่ละภูมิภาคตามพื้นที่สามารถแสดงข้อมูลได้ดังนี้

1.1 Central

![image](https://user-images.githubusercontent.com/115800837/196229677-48fee1c3-ca09-4801-bf83-c6ad8576196f.png)

1.2 East

![image](https://user-images.githubusercontent.com/115800837/196229744-047094e1-b995-462d-babb-3517da9dc5b7.png)

1.3 North

![image](https://user-images.githubusercontent.com/115800837/196229843-5ffeb234-f36f-41d0-92f4-cf2c1f459730.png)

1.4 North-East

![image](https://user-images.githubusercontent.com/115800837/196229885-5c44263c-18a0-47af-a26c-069e9bb062d7.png)

1.5 West

![image](https://user-images.githubusercontent.com/115800837/196229951-2e0fb070-d86f-48f6-a10a-8274dcab4367.png)


#### 2. Q: รูปแบบการให้บริการที่จอดรถแยกในด้านอื่นๆเป็นอย่างไร?

ข้อมูลแสดงสัดส่วนจำนวนที่จอดรถฟรีแยกตามภูมิภาค

![image](https://user-images.githubusercontent.com/115800837/196241814-6ff31d0a-bbe4-4cc3-beda-7fb4e24e452a.png)

ข้อมูลแสดงสัดส่วนจำนวนที่จอดรถที่สามารถฟรีและจอดรถตอนกลางคืน

![image](https://user-images.githubusercontent.com/115800837/196232213-9ca84bc6-7ebe-4ca4-ba72-15f6afca9ca9.png)


A: จากข้อมูลสรุปได้ว่ามีแนวโน้มที่ค่อนข้างดี เนื่องจาก จากข้อมูลในข้อ1 จะพบว่า (1.) ครอบคลุมทั่วทุกภูมิภาค (2.)เป็นระบบ electronic เกือบทั้งหมด และจากข้อมูลที่แสดงในกราฟข้อ 2 จะพบว่า (3.) แต่ละภูมิภาคจอดฟรีมากกว่า 60% ในแต่ละภูมิภาค และมีที่จอดจอดฟรีและจอดกลางคืนมากกว่า 60% จากจำนวนที่จอดรถทั้งหมดเช่นกัน

#### 3. Q: หากต้องมีการพัฒนาเพิ่มเติมควรพัฒนาอะไรเพิ่มเติม?

![image](https://user-images.githubusercontent.com/115800837/196241678-07e7a172-0cfb-4d4d-8c99-c25d2870bc0d.png)
![image](https://user-images.githubusercontent.com/115800837/196240367-62373274-041b-433f-b762-50b49dea504c.png)


A: จากข้อมูลพบว่า ส่วนใหญ่เป็นลานจอดรถกลางแจ้ง(SURFACE CAR PARK)เกือบ 50% หากเป็นไปได้ควรพัฒนาให้เป็นที่จอดรถที่มีหลังคาหรือโครงสร้างปกติ(COVERD CAR PARK) หรือ ในอนาคตอาจเพิ่มจำนวนที่จอดรถอัจฉริยะ(MACHANISED CAR PARK) หรือ ที่จอดรถใต้ดิน (BASEMENT CAR PARK) เนื่องจากมีสัดส่วนประมาณ 2% เมื่อเทียบจากจำนวนที่จอดรถทั้งหมด

# Challenge
- หาข้อมูลที่เป็นข้อมูลจริงที่มีข้อมูลให้วิเคราะห์ได้หลากหลายค่อนข้างลำบาก อาจเพราะไม่มีมีประสบการณ์หรือมีความรู้เกี่ยวกับ Open Public Data source ยังน้อย
- การ Merge ข้อมูลระหว่าง ข้อมูลรายละเอียด ต้องมีการ Cleansing ข้อมูลที่อยู่ที่เป็น freetext ยาวๆ และ Pattern ไม่เหมือนกัน ส่งผลให้ยากต่อการ cleansing และใช้เวลานานมาก
- แสดงข้อมูลที่มีรายละเอียดได้มากกว่านี้แต่ยังไม่ชำนาญในการแปลงเป็น code 
- กรณีที่ต้องวิเคราะห์เพิ่มเติมอยากจะเจาะลึกถึงความสัมพันธ์ของจำนวนประชากรในแต่ละพื้นที่เมื่อเทียบกับจุดให้บริการจอดรถ(ซึ่งต้องหา Dataset ข้อมูลประชากรตามพื้นที่เพิ่มเติม) หรือ กรณีที่ต้องเก็บค่าจอดเพิ่มควรโฟกัสพื้นที่ไหนเป็นพิเศษ? (ซึ่งต้องหา Dataset ข้อมูลการใช้บริการและเรทค่าจอดรถเพิ่มเติม)
- (เพิ่มเติมจาก comment อาจารย์) : สามารถวิเคราะห์ข้อมูลเปรียบเทียบที่จอดของประเทศอื่นว่ามีความแตกต่างกัน หรือไม่

# Summary Infographic

![S__2457620](https://user-images.githubusercontent.com/115800837/205315713-33015713-1e6b-4e2c-aedf-a2181cc00eac.jpg)

