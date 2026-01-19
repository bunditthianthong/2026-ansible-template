

# สร้าง virtual environment ที่ home/deploy ไปเลยใช้ร่วมกันได้
python3 -m venv ~/ansible-venv

# เปิดใช้งาน virtual environment
source ~/ansible-venv/bin/activate

# อัพเกรด pip
pip install --upgrade pip

# ติดตั้ง Ansible เวอร์ชันเสถียร
pip install ansible

# ตรวจสอบการติดตั้ง
ansible --version


--------------------------

# login root สร้างพาสเวิร์ดง่ายๆ test
sudo passwd deploy

# ใช้ GitBash 
# check กุญแจ
ls ~/.ssh/id_rsa.pub

# สร้าง กุญแจจากเครื่อง ตอนนี้เพื่อเข้าถึงจากเครื่องนี้
ssh-keygen -t rsa -b 4096

# ส่ง กุญแจ
# จะมีถามอะไรไม่รู้ คำถามแรก ท้ายๆ มีคำว่า finger print แต่ใส่ yes จะถามพาสเวิร์ดใส่พากเวิร์ด
ssh-copy-id deploy@192.168.52.22


# ทดสอบ ssh จะเข้าได้เลยไม่ต้องใส่พาสเวิร์ด และ sudo ไม่ถามพาสเวิร์ด
ssh deploy@192.168.52.22

whoami

sudo hostname


# ลบรหัสผ่านของ user deploy (ทำให้ login ด้วย password ไม่ได้อีกต่อไป ต้องใช้ key เท่านั้น)
sudo passwd -d deploy

# เปิดพาสเวิร์ดกลับ
sudo passwd deploy