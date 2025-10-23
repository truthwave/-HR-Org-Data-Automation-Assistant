<img width="1536" height="1024" alt="人事" src="https://github.com/user-attachments/assets/46839172-c2d7-4918-af0f-9a8435dec0ec" /># HR/Department/Position Data Processing Assistant

> **Register maintenance: 60 minutes → 8 minutes.**
> Position verification: Manual → Automated.
> HR can focus solely on decision-making.


👉[ Try it now with ChatGPT](https://chatgpt.com/g/g-686cbd4b28c881918e461fb62a7e3c32-ren-shi-bu-shu-yi-zhi-tetachu-li-asisutanto)

<p align="center">
<img width="1536" height="1024" alt="人事" src="https://github.com/user-attachments/assets/c931319e-f4bd-467c-98f6-5101a009be01" />
</p>

---

## Experience (Completed in 3 Steps)
- **Formatting**: Automatically proposes CSV/column design and code systems (e.g., employee ID/department code/position code)
- **Verification**: Generates **constraint logic** (e.g., Department Head = 1 person per department, Section Chief = 1 person per section) in MUMPS/SQL/Python
- **Integration**: Output duplicate detection, master data reconciliation, and difference reports in **tables/JSON/procedures**

---

## Before → After

- Register maintenance: 60 min → 8 min
- Position rule checks: 0 min (automated)
- Initial duplicate integration: Half day → 20 min
> *Estimated. May vary based on environment and data quality.

---

## 📸Experience Image

![Demo](https://github.com/truthwave/-HR-Org-Data-Automation-Assistant/blob/main/English/Demo%20Movie.gif)

---

## Usage Example (Short Text)

**Position Restriction Logic (MUMPS Framework)**
Prerequisite: Assumes existence of position index ^EMPIDX(“ROLE”,dept,sec,title,empId).

> ; 1=Allow / 0=Deny
> CHKROLE(DEPT,SEC,TITLE)
>   NEW CNT,ID SET CNT=0,ID=“”
>   FOR  SET ID=$ORDER(^EMPIDX(“ROLE”,DEPT,SEC,TITLE,ID)) Q:ID=“”  SET CNT=CNT+1
>   QUIT $SELECT(TITLE=“Director”:CNT<1, TITLE="Deputy Director":CNT<1, TITLE="Section Chief":CNT<1, TITLE="Section Chief Proxy":CNT<1, 1:1)

**CSV Layout (Minimal)**
| Field           | Type      | Required | Example      |
| ------------ | ------ | --- | ------- |
| employee_id  | string | Yes | E000123 |
| dept_code    | string | Yes | D120    |
| section_code | string | No  | S07     |
| title_code   | string | Yes | MGR     |
| full_name    | string | Yes | Yamada Taro   |

---

## Usage (3 Steps)
1. Paste current **column names/code tables/business rules**<br>
2. Specify target state (**unique constraints/title limits/naming conventions**)<br>
3. Immediately implement/validate using generated **design/logic/validation procedures**

---

## Technical Notes

- **Prompt Design**: Normalize HR rules and output in order: constraints → validation → exception handling
- **MUMPS Support**: Combining **record count checks and unique constraints** is recommended, assuming index design
- **Security**: Do not input real data; validate using **fictitious data**

---

## Caution

- Do not input actual **personal information**
- Outputs are for **reference** only. Implementation requires expert review

## 🧑‍💻 Author

**[Truth Wave ― 真理の波](https://github.com/truthwave)**  

Please also check out information about my portfolio and AI tool development!

## Feel free to contact me
[📩 Inquiries & Quotes](mailto:realmadrid71214591@gmail.com)

---

> **Don't embellish. Leave only the constraints and the results.**
 
