<div align="center">

# 『 🐳 𝕎𝕙𝕒𝕝𝕖𝕏 𝕋-ℝ𝕖𝕩 🦖 』
### Next-Gen Enterprise SAP S/4HANA Cloud Ecosystem & Clean Core Architecture

<p align="center">
  <a href="https://github.com/WhaleXTrex"><img src="https://img.shields.io/badge/SAP-S%2F4HANA%20Cloud-008FD3?style=for-the-badge&logo=sap&logoColor=white" alt="SAP S/4HANA Cloud" /></a>
  <a href="https://github.com/WhaleXTrex"><img src="https://img.shields.io/badge/ABAP%20Cloud-Language%20Version%205-0070F3?style=for-the-badge&logo=sap&logoColor=white" alt="ABAP Cloud Version 5" /></a>
  <a href="https://github.com/WhaleXTrex"><img src="https://img.shields.io/badge/SAPUI5-v1.120+-E35205?style=for-the-badge&logo=sap&logoColor=white" alt="SAPUI5" /></a>
  <a href="https://github.com/WhaleXTrex"><img src="https://img.shields.io/badge/Clean%20Core-100%25%20Compliance-2EA44F?style=for-the-badge" alt="Clean Core" /></a>
  <a href="https://github.com/WhaleXTrex"><img src="https://img.shields.io/badge/CI%2FCD-abapGit%20%7C%20gCTS-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git CI/CD" /></a>
</p>

<p align="center">
  <em>"Unleashing deep-ocean throughput with prehistoric strength."</em><br/>
  <strong>WhaleXTrex</strong> delivers high-performance, modular, and enterprise-grade cloud solutions for <strong>SAP S/4HANA Cloud</strong>,<br/>
  unifying Event-Driven Interfaces, Industrial Warehouse RF Terminals, Thai Statutory Tax Localization, Electronic Banking, and Master Forms.
</p>

---

</div>

## 🌌 สถาปัตยกรรมระดับองค์กร (Enterprise Architecture Overview)

```mermaid
graph TB
    subgraph UX["🎨 Modern User Experience Layer (SAP Fiori / UI5 Monorepos)"]
        UI_INT["🔗 Fiori Integration (16 Apps)"]
        UI_UTL["⚙️ Fiori Utilities (15 Apps)"]
        UI_HND["📱 Fiori Handheld Mobile (8 Apps)"]
        UI_THL["🇹🇭 Fiori Thai Localization (22 Apps)"]
        UI_PMT["💳 Fiori Payment File Manager"]
    end

    subgraph CORE["⚡ Clean Core ABAP Cloud Backend (RAP EML / OData V4)"]
        BO_INT["Whale Interface Framework<br/>(Staging API & Job Engine)"]
        BO_UTL["Whale Common Utilities<br/>(VarConf, Running No, Archive)"]
        BO_HND["Whale Handheld Solution<br/>(15 Industrial Barcode Modules)"]
        BO_THL["Thai Tax & Accounting Engine<br/>(WHT, Vouchers, Statements)"]
        BO_PMT["Bank Payment Engine<br/>(DMEE / PMW Bank BAdIs)"]
    end

    subgraph DOCS["📑 Master Document & Output Management"]
        XDP["56 Adobe LiveCycle Form Suites (.XDP)<br/>FI, MM, PM, PP, QM, SD + 9 Major Bank Cheques"]
    end

    subgraph DEPLOY["🚢 DevOps & Lifecycle Automation"]
        GCTS["SAP gCTS JSON Serialization (Format 6)<br/>Spaces, Pages, Catalogs, BSP & Semantic Roles"]
        AGIT["abapGit Serialization (Language Version 5)<br/>Clean Core CDS Views, Tables & Classes"]
    end

    UX <==>|OData V4 (JSON / Batch)| CORE
    CORE --> DOCS
    DEPLOY -.->|Continuous Deployment| CORE
    DEPLOY -.->|Launchpad Activation| UX
```

---

## 🏛️ สารบัญคลังโค้ด 14 Repositories (Repository Directory)

เราจัดระเบียบโครงสร้างตามมาตรฐาน **Enterprise 3-Tier Cloud Architecture** (แยก Backend, Frontend และ Deployment Artifacts เพื่อความคลีน 100%):

### 1. 🔗 Interface & Integration Suite
> โครงสร้างพื้นฐานสำหรับเชื่อมต่อระบบภายนอก (E-Commerce, POS, 3PL, WMS) เข้ากับ SAP S/4HANA Cloud ผ่าน OData V4 Staging และ Application Job Processor

| Repository | Role | รายละเอียดและจุดเด่น |
|---|:---:|---|
| [**`abap_integration`**](https://github.com/WhaleXTrex/abap_integration) | ⚡ Backend | Clean Core Interface Framework, Staging Inbound APIs, Outbound Event Engine, EML Logging |
| [**`fioriapp_integration`**](https://github.com/WhaleXTrex/fioriapp_integration) | 🎨 Frontend | **16 Fiori Monitoring Applications** สำหรับฝ่ายไอทีและผู้ดูแลระบบตรวจสอบ Payload และสั่ง Reprocess |
| [**`abap_integration_ui`**](https://github.com/WhaleXTrex/abap_integration_ui) | 🚢 Deployment | SAP gCTS Objects สำหรับลงทะเบียน Launchpad Spaces, Pages และ Security Roles |

---

### 2. ⚙️ Utilities & Common Tools Suite
> คลังเครื่องมือส่วนกลาง (Reusable Engines) ที่ทุกโมดูลในระบบสามารถเรียกใช้ร่วมกันได้

| Repository | Role | รายละเอียดและจุดเด่น |
|---|:---:|---|
| [**`abap_utilities`**](https://github.com/WhaleXTrex/abap_utilities) | ⚡ Backend | **8 Modules:** Variable Config (ZWHALEC_VARCONF), Document Running Number Engine, Archive & Purge |
| [**`fioriapp_utilities`**](https://github.com/WhaleXTrex/fioriapp_utilities) | 🎨 Frontend | **15 Fiori Applications** เช่น หน้าจอตั้งค่าพารามิเตอร์ระบบ, ตั้งรอบเลขที่เอกสาร, ล้างประวัติ Log |
| [**`abap_utilities_ui`**](https://github.com/WhaleXTrex/abap_utilities_ui) | 🚢 Deployment | Launchpad Catalog Definitions และ BSP Registrations สำหรับกลุ่มงาน Utilities |

---

### 3. 📱 Industrial RF Handheld Suite (Warehouse & Shop Floor)
> โซลูชันสแกนเนอร์บาร์โค้ดพกพาสำหรับงานคลังสินค้าและสายการผลิต รองรับ Zebra, Honeywell, Datalogic ตอบสนองระดับ Sub-second

| Repository | Role | รายละเอียดและจุดเด่น |
|---|:---:|---|
| [**`abap_handheld`**](https://github.com/WhaleXTrex/abap_handheld) | ⚡ Backend | **15 Barcode Modules:** GR with PO, GI to Prod, Prod Confirm, Picking for DO, SLoc Transfer, Label Print |
| [**`fioriapp_handheld`**](https://github.com/WhaleXTrex/fioriapp_handheld) | 🎨 Frontend | **8 Mobile RF Apps** ออกแบบปุ่มกดและ UI ขนาดใหญ่สำหรับใช้งานด้วยมือเดียว พร้อมเสียงแจ้งเตือน Beep |
| [**`abap_handheld_ui`**](https://github.com/WhaleXTrex/abap_handheld_ui) | 🚢 Deployment | gCTS Business Roles & Catalogs สำหรับพนักงานคลังสินค้า (Warehouse Operator) |

---

### 4. 🇹🇭 Thai Statutory Localization Suite
> โซลูชันงานบัญชี ภาษี และข้อกำหนดทางกฎหมายของประเทศไทย (กรมสรรพากร) ครบถ้วนตามมาตรฐาน

| Repository | Role | รายละเอียดและจุดเด่น |
|---|:---:|---|
| [**`abap_thlocalization`**](https://github.com/WhaleXTrex/abap_thlocalization) | ⚡ Backend | **5 Packages:** ภาษีหัก ณ ที่จ่าย (WHT), ใบสำคัญ 8 ประเภท (AP/AR/AS/BV/IV/JV/PV/RV), ใบวางบิล, ใบเสร็จ |
| [**`fioriapp_thlocalization`**](https://github.com/WhaleXTrex/fioriapp_thlocalization) | 🎨 Frontend | **22 Fiori Applications Monorepo** ทั้งระบบออกใบเสร็จ, จัดการที่อยู่สาขา และ SD Mass Printing (Billing, DO, SO) |
| [**`abap_thlocalization_ui`**](https://github.com/WhaleXTrex/abap_thlocalization_ui) | 🚢 Deployment | SAP gCTS Fiori Catalogs และ Launchpad Layouts ฝั่งบัญชีและการเงิน |

---

### 5. 📄 Master Adobe LiveCycle Forms Library
> คลังไฟล์แบบฟอร์มเอกสารทางธุรกิจสำเร็จรูปพร้อมพิมพ์ สวยงาม คมชัด และรองรับภาษาไทย 100%

| Repository | ประเภท | รายละเอียดและจุดเด่น |
|---|:---:|---|
| [**`whale_adobe_forms`**](https://github.com/WhaleXTrex/whale_adobe_forms) | 📄 Assets (.xdp/.xsd) | **56 Form Suites:**<br/>• **FI:** ใบสำคัญ 13 รูปแบบ, ใบวางบิล, ใบเสร็จรับเงิน, ใบลดหนี้/เพิ่มหนี้<br/>• **Bank Cheques:** รูปแบบเช็คสั่งจ่าย **9 ธนาคารพาณิชย์ชั้นนำ** (BBL, KBANK, SCB, KTB, BAY, TTB, UOB, CITIBANK, LH)<br/>• **MM / PM / PP / QM / SD:** ใบสั่งซื้อ (PO), ใบส่งของ (DO), สั่งผลิต, นับสต็อก, COA, สัญญาขาย |

---

### 6. 💳 Corporate Electronic Banking & Payment Suite
> ระบบจัดการไฟล์สั่งจ่ายเงินอิเล็กทรอนิกส์เข้าสู่ระบบธนาคารพาณิชย์ (Direct Credit / Payroll / Supplier Transfer)

| Repository | Role | รายละเอียดและจุดเด่น |
|---|:---:|---|
| [**`abap_payment-fioriapp_payment`**](https://github.com/WhaleXTrex/abap_payment-fioriapp_payment) | ⚡ + 🎨 Fullstack | **DMEE / PMW Engine:** BAdI 06, 21 สำหรับ Custom Bank Format (K-Cash, iCash, Anywhere)<br/>**Fiori UI:** แอปพลิเคชัน `paymentfile` (`PYF001`) สำหรับดาวน์โหลดและติดตามสถานะไฟล์ |

---

## 💎 ปรัชญาการพัฒนา Clean Core (Our Core Principles)

1. **Strict ABAP Cloud (Language Version 5):**
   - โค้ดทั้งหมดใช้คำสั่งมาตรฐาน ABAP Cloud ปราศจากคำสั่ง Obsolete
   - เข้าถึงข้อมูลผ่าน Released CDS Views และเรียกใช้งานผ่าน RAP EML (`MODIFY ENTITIES OF...`) เท่านั้น
2. **Zero Modification Guarantee:**
   - ไม่มีการแก้ไข SAP Standard Table หรือ Core Code แม้แต่บรรทัดเดียว
   - ทำให้ระบบสามารถอัปเกรดเวอร์ชัน SAP S/4HANA Cloud (เช่น 2402 ➔ 2408 ➔ 2502) ได้อย่างราบรื่นโดยไม่เกิดผลกระทบ (Upgrade-Safe)
3. **Automated Monorepo Cleanliness:**
   - Fiori Frontend ทุกตัวมีระบบ Clean Tooling ในตัว ปราศจากไฟล์ส่วนเกิน
   - โครงสร้างแยกตามมาตรฐาน Namespace สากล `whalecloud.app.*` และ `ZWHALEC_*`

---

## 🤝 ร่วมงานและติดต่อ (Get in Touch)

องค์กร **WhaleXTrex** มุ่งมั่นพัฒนามาตรฐานใหม่สำหรับโซลูชันองค์กรระดับสากล  
หากต้องการร่วมพัฒนา แนะนำข้อเสนอแนะ หรือมีข้อสงสัยเกี่ยวกับสถาปัตยกรรม:

- 🌐 **GitHub Organization:** [https://github.com/WhaleXTrex](https://github.com/WhaleXTrex)
- 🏢 **Ecosystem:** WHALE Cloud Enterprise Solutions

<div align="center">
  <br/>
  <sub>Developed with ❤️ by <strong>WhaleXTrex Team</strong>. All rights reserved.</sub>
</div>
