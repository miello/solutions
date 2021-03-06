ข้อนี้ในการดึงเชือกแต่ละครั้งจะมีการลดความยาวของเชือกจากทางด้านซ้ายและขวาเท่า ๆ กัน ดังนั้นเราจึงต้องการโครงสร้างข้อมูลที่สามารถทำงานเหล่านี้ได้ในเวลาเร็ว ๆ
- ตอบค่าที่ช่อง ๆ หนึ่ง (point query)
- หาผลรวมของช่วง ๆ หนึ่ง (range query)
- เปลี่ยนค่าที่ช่อง ๆ หนึ่ง (point update)
- เปลี่ยนค่าช่วง ๆ หนึ่งให้กลายเป็น 0 (range update)

โครงสร้างข้อมูลชนิดหนึ่งที่สามารถทำงานเหล่านี้ได้เร็ว ๆ คือ segment tree with lazy propagation ซึ่งสามารถทำงานแต่ละอย่างในนี้ได้ใน $\mathcal{O}(logN)$ 

ในการดึงเชือกแต่ละครั้ง ให้ point update ที่ช่อง ๆ นั้นเพิ่มด้วยความยากเชือกที่ดึง จากนั้นให้หาว่าจะเชือกจะถูกดึงไปถึงช่วงที่เท่าไหร่ในทางซ้าย แล้วเปลี่ยนช่วงเหล่านั้นให้กลายเป็น 0 และทำเช่นนี้สำหรับทางขวาด้วย การทำเช่นนี้ ให้เราทำการ binary search บนช่องเหล่านั้น ทำให้เราได้อัลกอริธึมที่สามารถแก้โจทย์นี้ได้ใน $\mathcal{O}(Nlog^2N)$

อัลกอริธึมนี้สามารถพัฒนาให้ดีขึ้นได้ โดยแทนที่เราจะ binary search ให้เราเลือก traverse ลงไปใน segment tree เพื่อหาว่าเชือกจะดึงไปถึงช่องที่เท่าไหร่ time complexity ของอัลกอริธึมเราจึงเป็น $\mathcal{O}(NlogN)$