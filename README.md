# abap-webdynpro-leave-request
Leave Request Application using Web DYNPRO
# SAP Web Dynpro ABAP - Dynamic Leave Request Application (`ZJT_WD_LEAVE`)

A custom SAP Web Dynpro ABAP leave management application featuring dynamic, role-based UI controls via URL parameters (`ROLE=EMP` vs `ROLE=ADMIN`).

---

## 🚀 Key Features

- **Dynamic Role-Based UI:** Toggles action visibility dynamically based on URL execution parameters:
  - **`ROLE=EMP` (Employee View):** Displays **Create** and **Edit** action buttons.
  - **`ROLE=ADMIN` (Approver View):** Hides employee actions and exposes **Approve** and **Reject** buttons.
- **Leave Requests Overview:** Interactive table (`V_LIST`) displaying leave status, employee details, timestamps, and approver remarks.
- **Context-Bound Visibility Control:** Driven by dedicated `WDUI_VISIBILITY` attributes (`SAVE_VISIBLE`, `ADMIN_VISIBLE`) mapped through the Component Controller.
- **Modular Architecture:** Utilizes clean separation of concerns across Windows, Views, and Assistance Classes (`ZCL_JT_WD_LEAVE_ASSIST`).

---

## 🛠️ Technical Architecture

| Component Object | Object Name | Purpose |
| :--- | :--- | :--- |
| **Component** | `ZJT_WD_LEAVE` | Main Web Dynpro Component |
| **Application** | `ZJT_WD_LEAVE_APP` | Application endpoint for web invocation |
| **Window** | `W_MAIN` (`ZJT_WD_LEAVE`) | Main window handling `HANDLEDEFAULT` URL event parameters |
| **Views** | `V_LIST`, `V_DETAIL` | Request list overview and detail maintenance views |
| **Assistance Class** | `ZCL_JT_WD_LEAVE_ASSIST` | Business logic, DB operations, and status processing |

---

## 🔗 URL Execution Formats

To test the role-based visibility, append the `ROLE` parameter to your Web Dynpro application URL:

- **Employee Portal:**
  ```text
  https://<your-sap-server>/sap/bc/webdynpro/sap/zjt_wd_leave_app?sap-client=100&ROLE=EMP#
  https://<your-sap-server>/sap/bc/webdynpro/sap/zjt_wd_leave_app?sap-client=100&ROLE=ADMIN#
