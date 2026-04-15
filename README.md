[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=23574219&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** baonguyengia2701@gmail.com
**Name:** Nguyễn Gia Bảo

---

## Mo ta

Bai lab xay dung mot ETL Pipeline tu dong xu ly du lieu san pham tu file JSON. Pipeline thuc hien cac buoc: Extract du lieu tu file JSON, Validate de loai bo cac record khong hop le (gia am hoac category rong), Transform de chuan hoa du lieu (tinh gia giam 10%, chuan hoa category Title Case, them timestamp), va Load ket qua ra file CSV. Ngoai ra, bai lab con thi nghiem so sanh hieu qua cua AI Agent khi lam viec voi Clean Data va Garbage Data de chung minh tam quan trong cua chat luong du lieu.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### Chay ETL Pipeline
```bash
python solution.py
```
Sau khi chay, file `processed_data.csv` se duoc tao ra voi 3 records hop le.

### Chay Agent Simulation (Stress Test)

**Buoc 1:** Tao garbage data
```bash
python generate_garbage.py
```

**Buoc 2:** Chay agent simulation voi ca 2 loai du lieu
```bash
python agent_simulation.py
```

**Clean Data:** Agent tra loi chinh xac — goi y Laptop $1200.
**Garbage Data:** Agent tra loi sai — goi y Nuclear Reactor $999999 do outlier cuc doan.

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline (3 records hop le)
├── garbage_data.csv         # Du lieu loi dung cho stress test
├── generate_garbage.py      # Script tao garbage data
├── agent_simulation.py      # Simulation AI Agent voi 2 loai du lieu
├── experiment_report.md     # Bao cao thi nghiem va phan tich
├── raw_data.json            # Du lieu nguon (5 records, 2 bi loai)
└── README.md                # File nay
```

---

## Ket qua

- **Tong so records trong raw data:** 5
- **Records hop le (processed):** 3 (Laptop, Chair, Monitor)
- **Records bi loai (dropped):** 2
  - Record id=3 (Mystery Box): price = -10 (gia am)
  - Record id=4 (Phone): category = "" (category rong)
- **Output:** `processed_data.csv` voi cac cot: id, product, price, category, discounted_price, processed_at
