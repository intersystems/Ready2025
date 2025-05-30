
# FHIR Workshop for Ready 2025

Welcome to the official training repository for the **FHIR Workshop for Ready 2025**. This workshop is designed to guide developers through practical exercises using **FHIRPath** and **FHIR SQL Builder** in a locally hosted FHIR development environment.

## 🚀 Getting Started

To follow the exercises, you need to set up a local development environment.

### 🔧 Environment Setup

You’ll need the following tools:

- Docker
- VS Code
- Python
- Jupyter Notebooks
- [IRIS for Health Community Edition 2025.1](https://community.intersystems.com/post/fhir-environment-setup-guide) (with a pre-configured FHIR server and sample patients)

For setup instructions, refer to:
- [Windows setup video](https://youtu.be/IyvuHbxCwCY)
- [macOS setup video](https://youtu.be/Ss7vU0l3JNU)

Clone this repository into your development directory:

```bash
git clone https://github.com/intersystems/Ready2025.git
```

Make sure your Docker container is running. Verify that the FHIR server is operational:

```http
GET http://127.0.0.1:8080/csp/healthshare/demo/fhir/r4/metadata
```

If a CapabilityStatement is returned, you're good to go!

---

## 🧪 FHIRPath Exercise

Navigate to the Jupyter notebook:  
`FHIRPath/Fhirpath1.ipynb`

> Ensure your FHIR server is running (`docker ps` and check metadata endpoint).  
> **Note:** `FHIRPath/Fhirpath2.ipynb` is optional.

---

## 🛠️ FHIR SQL Builder Exercise

### Access the FHIR SQL Builder UI:
[http://127.0.0.1:8080/csp/fhirsql/index.html](http://127.0.0.1:8080/csp/fhirsql/index.html)

#### Login:
- **Username**: `_SYSTEM`  
- **Password**: `ISCDEMO`

### Steps Overview:

1. **Create a Repository Configuration**
   - Host: `127.0.0.1`
   - Port: `52773`
   - Repository URL: `/csp/healthshare/demo/fhir/r4`
   - Credentials: Use `_SYSTEM / ISCDEMO`

2. **Launch Analysis Task**
   - Analyze 100% of ~70K resources

3. **Create Transformations**
   - `pt_transform`:  
     `"ID", "BirthDate", "FirstName", "Gender", "LastName", "LastUpdated", "MaritalStatus", "PatientBirthPlaceCity"`
   - `allergy_transform`:  
     `"ID", "AllergyCode", "AllergyDisplay", "LastUpdated", "PatientReference"`

4. **Create Projections**
   - `pt_transform` → SQL Package: `sql1`  
   - `allergy_transform` → SQL Package: `sql2`

5. **View SQL Tables**  
   Access via Management Portal:
   ```
   http://127.0.0.1:8080/csp/sys/exp/%25CSP.UI.Portal.SQL.Home.zen?$NAMESPACE=DEMO
   ```

📺 **Watch the step-by-step video**: [https://bcove.video/4iRIDN8](https://bcove.video/4iRIDN8)

---

## 📊 Data Analysis with Python

Open the notebook:  
`FHIRAnalytics/AlllergyInterolerance.ipynb`

- Learn to query the projected FHIR data using the InterSystems Python db-api driver.
- Perform data analysis and exploration.

---

## 🧠 Additional Resources

- [FHIR Environment Setup Guide](https://community.intersystems.com/post/fhir-environment-setup-guide)
- [Docker Documentation](https://docs.docker.com/)
- [Python DB-API with InterSystems](https://docs.intersystems.com/irislatest/csp/docbook/Doc.View.cls?KEY=GBJDB)

---

## 💬 Support

If you encounter any issues or have questions, please open an [Issue](https://github.com/intersystems/Ready2025/issues) in this repository or post on the [InterSystems Developer Community](https://community.intersystems.com).

---

Happy FHIR-ing! 🔥
