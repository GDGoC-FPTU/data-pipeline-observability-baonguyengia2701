# Experiment Report: Data Quality Impact on AI Agent

**Student ID:** AI20K-2A202600156
**Name:** Nguyễn Gia Bảo
**Date:** 2026-04-15

---

## 1. Ket qua thi nghiem

Chay `agent_simulation.py` voi 2 bo du lieu va ghi lai ket qua:

| Scenario | Agent Response | Accuracy (1-10) | Notes |
|----------|----------------|-----------------|-------|
| Clean Data (`processed_data.csv`) | "Based on my data, the best choice is Laptop at $1200." | 9 | Ket qua chinh xac, Laptop la san pham electronics co gia hop ly nhat |
| Garbage Data (`garbage_data.csv`) | "Based on my data, the best choice is Nuclear Reactor at $999999." | 1 | Ket qua sai hoan toan, Agent bi danh lua boi outlier cuc doan |

---

## 2. Phan tich & nhan xet

### Tai sao Agent tra loi sai khi dung Garbage Data?

Agent tra loi sai khi su dung Garbage Data vi du lieu dau vao chua nhieu van de nghiem trong ve chat luong. Thu nhat, bo du lieu garbage co Duplicate ID (ca hai record id=1 deu ton tai), khien Agent bi nham lan ve so luong san pham thuc su. Thu hai, record "Nuclear Reactor" voi gia $999,999 la mot outlier cuc doan, gia tri bat thuong nay khong bi loc bo nen khi Agent tim san pham electronics co gia cao nhat, no tra ve ket qua hoan toan vo nghia trong thuc te. Thu ba, record "Broken Chair" co truong price la chuoi "ten dollars" thay vi so, gay ra loi kieu du lieu co the lam hong logic tinh toan. Ngoai ra, record voi Null ID va gia = 0 la du lieu khong hop le nhung van duoc Agent xu ly, dan den ket qua khong chinh xac. Tat ca nhung van de tren cho thay rang neu khong co buoc Validate du lieu truoc khi dua vao Agent, he thong co the tra ve nhung ket qua sai lech nguy hiem, du cho prompt co chinh xac den dau cung khong the kiem soat duoc chat luong cua output.

---

## 3. Ket luan

**Quality Data > Quality Prompt?** Dong y.

Du lieu sach va chinh xac quan trong hon mot prompt hoan hao. Khi du lieu dau vao chua nhieu loi nhu outliers, null values, duplicate records hay wrong data types, Agent se tra loi sai bat ke prompt co duoc viet tot den dau. ETL Pipeline voi buoc Validate nghiem ngat chinh la lop bao ve quan trong nhat de dam bao chat luong output cua AI Agent. Garbage In = Garbage Out.
