# DADS5001_MiniProject_6420422011
ภาพรวมการให้บริการที่จอดรถของหน่วยงาน Singapore Housing & Development Board : มีการให้บริการที่ครอบคลุมเพียงพอหรือไม่ และเมื่อดูจาก Factor ต่างๆ มีจุดไหนที่สามารถพัฒนาได้หรือไม่?

# Overview : What's HDB?

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/hdbsite-logo.jpg)

HDB หรือ Housing & Development Board คือองค์กรหนึ่งของประเทศสิงคโปร์ที่ดูแลจัดการเกี่ยวกับที่อยู่อาศัย ซึ่งมีหน้าที่เป็นผู้วางแผนและพัฒนาที่อยู่อาศัยและปรับปรุงเปลี่ยนแปลงเมืองสิงคโปร์เพื่อให้ประชาชนทุกคนที่อยู่ในสิงคโปร์มีคุณภาพชีวิตที่ดี HDB สร้างย่านการค้าหลายรูปแบบ สถานที่พักผ่อนทำกิจกรรมนันทนาการ และสร้าง facility ในเมืองให้ประชาชนอยู่อาศัยอย่างสะดวกสบาย
ซึ่งในที่นี่เราจะมาสรุปภาพรวมของ 1 ใน Facility ของ HDB นั่นก็คือ การให้บริการที่จอดรถ ว่าเป็นอย่างไรดังรายละเอียดด้านล่างค่ะ :)

Credit : 
https://propholic.com/prop-globe/%E0%B9%80%E0%B8%A2%E0%B8%B5%E0%B9%88%E0%B8%A2%E0%B8%A1%E0%B8%8A%E0%B8%A1-hdb-hub-%E0%B8%81%E0%B8%B2%E0%B8%A3%E0%B9%80%E0%B8%84%E0%B8%AB%E0%B8%B0%E0%B8%AA%E0%B8%B4%E0%B8%87%E0%B8%84%E0%B9%82%E0%B8%9B/

# Dataset
1. Dataset ข้อมูลรายละเอียดจุดบริการที่จอดรถทั้งหมด 

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/source%20table3.JPG)
![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/source%20table1.JPG)

Source : https://data.gov.sg/dataset/hdb-carpark-information?view_id=398e65ae-e2cb-4312-8651-6e65d6f19ed1&resource_id=139a3035-e624-4f56-b63f-89ae28d4ae4c
- 2182 rows 
- 12 Columns : 
car_park_no, address, x_coord, y_coord, car_park_type, type_of_parking_system, short_term_parking, free_parking, night_parking, car_park_decks, gantry_height, car_park_basement

2. Dataset Planning Areas of Singapore

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/source%20table4.JPG)


Source : https://en.wikipedia.org/wiki/Planning_Areas_of_Singapore
- 55 rows 
- 9 Columns : 
Name (English) , Malay, Chinese, Pinyin, Tamil, Region, Area (km²), Population[7], Density (/km²)

# How to create
1. Load dataset & Cleansing : จากข้อมูล Datasetแรกพบว่าข้อมูลที่อยู่ค่อนข้างเป็น Freetext จึงต้องทำการ Cleansing ข้อมูลที่อยู่ เพื่อนำไปเชื่อมกับข้อมูล Region ใน Datasetที่ 2

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/cleansing.JPG)

2. Merging Dataset : หลังจากทำการ Merging ข้อมูล จะพบกว่าข้อมูลรายละเอียดของที่จอดรถมีข้อมูล Region เพิ่มเติม ซึ่งทำให้สามารถจัดกลุ่มข้อมูลตามภูมิภาคเพื่อประกอบการวิเคราะห์เทียบกับ Factor อื่นๆ

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/merging%20dataset.JPG)

3. Pvot & Visualization : นำข้อมูลจากข้อ 2 มา Pivot ในแง่มุมต่างๆ ตามตัวอย่างด้านล่าง และ ในหัวข้อถัดไปค่ะ

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/Pivot.JPG)


# Question & Answer
1. Q: การกระจายตัวของที่จอดรถในแต่ละภูมิภาคเป็นอย่างไร?

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/graph1.JPG)

A: จากกราฟข้อมูล Number of Car Park by Region and Payment System จะพบว่า Overall HDB จะมีการให้บริการทั่วทุกภูมิภาคกมากกว่า 2,000 จุด โดยกว่า 90% เป็นการให้บริการแบบ Electronic System โดยมีการใช้ Coupon System เพียงเล็กน้อยเท่านั้น 10%




2. Q: รูปแบบการให้บริการที่จอดรถแยกตามภูมิภาคดีและเพียงพอจริงหรือไม่?

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/graph3.JPG)

A: จากข้อมูลสรุปได้ว่าดีและเพียงพอ เนื่องจาก (1.) ครอบคลุมทั่วทุกภูมิภาค (2.)เป็นระบบ electronic เกือบทั้งหมด (3.)แต่ละภูมิภาคจอดฟรีมากกว่า 60%

3. Q: หากต้องมีการพัฒนาเพิ่มเติมควรพัฒนาอะไรเพิ่มเติม?

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/graph2.JPG)![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/table1.JPG)

A: จากข้อมูลพบว่า ส่วนใหญ่เป็นลานจอดรถกลางแจ้ง(SURFACE CAR PARK)เกือบ 50% หากเป็นไปได้ควรพัฒนาให้เป็นที่จอดรถที่มีหลังคาหรือโครงสร้างปกติ(COVERD CAR PARK) หรือ ในอนาคตอาจเพิ่มจำนวนที่จอดรถอัจฉริยะ(MACHANISED CAR PARK) หรือ ที่จอดรถใต้ดิน (BASEMENT CAR PARK) เนื่องจากมีสัดส่วนประมาณ 2% เมื่อเทียบจากจำนวนที่จอดรถทั้งหมด

# Other information

![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/table2.JPG)
![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/table3.JPG)
![image](https://github.com/Juntanep/DADS5001_MiniProject/blob/main/table4.JPG)

# Challenge
- หาข้อมูลที่เป็นข้อมูลจริงที่มีข้อมูลให้วิเคราะห์ได้หลากหลายค่อนข้างลำบาก อาจเพราะไม่มีมีประสบการณ์หรือมีความรู้เกี่ยวกับ Open Public Data source ยังน้อย
- การ Merge ข้อมูลระหว่าง ข้อมูลรายละเอียด ต้องมีการ Cleansing ข้อมูลที่อยู่ที่เป็น freetext ยาวๆ และ Pattern ไม่เหมือนกัน ส่งผลให้ยากต่อการ cleansing และใช้เวลานานมาก
- แสดงข้อมูลที่มีรายละเอียดได้มากกว่านี้แต่ยังไม่ชำนาญในการแปลงเป็น code หรือ visualized code
- กรณีที่ต้องวิเคราะห์เพิ่มเติมอยากจะเจาะลึกถึงความสัมพันธ์ของจำนวนประชากรในแต่ละพื้นที่เมื่อเทียบกับจุดให้บริการจอดรถ(ซึ่งต้องหา Dataset ข้อมูลประชากรตามพื้นที่เพิ่มเติม) หรือ กรณีที่ต้องเก็บค่าจอดเพิ่มควรโฟกัสพื้นที่ไหนเป็นพิเศษ? (ซึ่งต้องหา Dataset ข้อมูลการใช้บริการและเรทค่าจอดรถเพิ่มเติม)
- (เพิ่มเติมจาก comment อาจารย์) : สามารถวิเคราะห์ข้อมูลเปรียบเทียบที่จอดของประเทศอื่น เช่น ประเทศไทย ว่ามีความแตกต่างกัน หรือไม่
