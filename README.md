<!doctype html>
<html lang="ar" dir="rtl">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>منصة تقارير العمليات</title>
    <style>
      :root {
        --bg: #091117;
        --panel: rgba(13, 24, 32, 0.9);
        --panel-soft: rgba(17, 32, 43, 0.78);
        --line: rgba(160, 198, 178, 0.18);
        --text: #e9f4ef;
        --muted: #a8bbb0;
        --primary: #24b47e;
        --primary-strong: #1de29f;
        --accent: #c8a96b;
        --danger: #d76f6f;
        --shadow: 0 24px 60px rgba(0, 0, 0, 0.28);
      }

      * {
        box-sizing: border-box;
      }

      body {
        margin: 0;
        min-height: 100vh;
        font-family: "Segoe UI", Tahoma, Arial, sans-serif;
        background:
          radial-gradient(circle at top, rgba(36, 180, 126, 0.16), transparent 35%),
          linear-gradient(180deg, #071016 0%, #0a141b 45%, #081118 100%);
        color: var(--text);
      }

      .shell {
        width: min(1400px, calc(100% - 32px));
        margin: 0 auto;
        padding: 24px 0 40px;
      }

      .hero,
      .panel {
        background: var(--panel);
        border: 1px solid var(--line);
        border-radius: 22px;
        box-shadow: var(--shadow);
        backdrop-filter: blur(16px);
      }

      .hero {
        padding: 24px;
        display: grid;
        gap: 20px;
        grid-template-columns: 1.4fr 1fr;
      }

      .hero h1 {
        margin: 0 0 10px;
        font-size: clamp(28px, 3vw, 42px);
      }

      .hero p {
        margin: 0;
        color: var(--muted);
        line-height: 1.8;
      }

      .stats {
        display: grid;
        gap: 14px;
      }

      .stat {
        padding: 18px;
        background: var(--panel-soft);
        border: 1px solid rgba(200, 169, 107, 0.16);
        border-radius: 18px;
      }

      .stat-label {
        color: var(--muted);
        font-size: 14px;
        margin-bottom: 8px;
      }

      .stat-value {
        font-size: 28px;
        font-weight: 700;
      }

      .status-ready {
        color: var(--primary-strong);
      }

      .status-idle {
        color: var(--accent);
      }

      .service-grid {
        margin-top: 20px;
        display: grid;
        gap: 14px;
        grid-template-columns: repeat(4, minmax(0, 1fr));
      }

      .service-btn {
        border: 1px solid var(--line);
        border-radius: 20px;
        background: linear-gradient(180deg, rgba(14, 27, 35, 0.95), rgba(8, 17, 22, 0.95));
        color: var(--text);
        text-align: right;
        padding: 20px;
        cursor: pointer;
        transition: 0.25s ease;
      }

      .service-btn:hover {
        transform: translateY(-2px);
        border-color: rgba(36, 180, 126, 0.5);
      }

      .service-btn.active {
        border-color: rgba(36, 180, 126, 0.95);
        box-shadow: 0 0 0 1px rgba(36, 180, 126, 0.4), 0 12px 34px rgba(36, 180, 126, 0.16);
      }

      .service-btn strong {
        display: block;
        font-size: 20px;
        margin-bottom: 8px;
      }

      .service-btn span {
        color: var(--muted);
        font-size: 14px;
        line-height: 1.7;
      }

      .workspace {
        margin-top: 20px;
        display: grid;
        gap: 20px;
        grid-template-columns: minmax(0, 1.35fr) minmax(320px, 0.9fr);
      }

      .panel {
        padding: 22px;
      }

      .panel h2,
      .panel h3 {
        margin: 0 0 16px;
      }

      .forms > section {
        display: none;
      }

      .forms > section.active {
        display: block;
      }

      .fields {
        display: grid;
        gap: 12px;
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .fields-3 {
        display: grid;
        gap: 12px;
        grid-template-columns: repeat(3, minmax(0, 1fr));
      }

      .full {
        grid-column: 1 / -1;
      }

      label {
        display: block;
        font-size: 14px;
        color: var(--muted);
        margin-bottom: 6px;
      }

      input,
      select,
      textarea,
      button {
        font: inherit;
      }

      input,
      select,
      textarea {
        width: 100%;
        border-radius: 14px;
        border: 1px solid rgba(160, 198, 178, 0.18);
        background: rgba(6, 14, 18, 0.75);
        color: var(--text);
        padding: 12px 14px;
      }

      textarea {
        min-height: 86px;
        resize: vertical;
      }

      .mini-card {
        margin-top: 18px;
        padding: 16px;
        border-radius: 18px;
        background: rgba(8, 17, 23, 0.68);
        border: 1px solid rgba(160, 198, 178, 0.12);
      }

      .mini-grid {
        display: grid;
        gap: 12px;
        grid-template-columns: 0.9fr 0.9fr auto auto;
        align-items: end;
      }

      .action-row {
        margin-top: 18px;
        display: flex;
        flex-wrap: wrap;
        gap: 10px;
      }

      .btn {
        border: 0;
        border-radius: 14px;
        padding: 12px 18px;
        cursor: pointer;
      }

      .btn-primary {
        background: linear-gradient(135deg, var(--primary), #188f66);
        color: #04110b;
        font-weight: 700;
      }

      .btn-secondary {
        background: rgba(200, 169, 107, 0.18);
        color: #f7e2b9;
        border: 1px solid rgba(200, 169, 107, 0.24);
      }

      .btn-danger {
        background: rgba(215, 111, 111, 0.15);
        color: #ffcbcb;
        border: 1px solid rgba(215, 111, 111, 0.28);
      }

      .checkbox {
        display: flex;
        gap: 10px;
        align-items: center;
        margin-top: 12px;
        color: var(--text);
      }

      .checkbox input {
        width: 18px;
        height: 18px;
      }

      .list {
        display: grid;
        gap: 10px;
        margin-top: 14px;
      }

      .list-item {
        background: rgba(7, 15, 20, 0.82);
        border: 1px solid rgba(160, 198, 178, 0.14);
        border-radius: 16px;
        padding: 12px 14px;
        display: flex;
        justify-content: space-between;
        gap: 10px;
        align-items: center;
      }

      .list-item small {
        color: var(--muted);
        display: block;
        margin-top: 4px;
      }

      .preview-box {
        min-height: 720px;
        white-space: pre-wrap;
        line-height: 1.9;
        background: rgba(6, 13, 18, 0.78);
        border-radius: 18px;
        border: 1px solid rgba(160, 198, 178, 0.12);
        padding: 18px;
        overflow: auto;
      }

      .notice {
        margin-top: 12px;
        color: var(--muted);
        font-size: 14px;
      }

      .hidden {
        display: none;
      }

      @media (max-width: 1180px) {
        .service-grid,
        .fields-3,
        .workspace,
        .hero {
          grid-template-columns: 1fr;
        }

        .fields,
        .mini-grid {
          grid-template-columns: 1fr;
        }

        .preview-box {
          min-height: 440px;
        }
      }
    </style>
  </head>
  <body>
    <div class="shell">
      <section class="hero">
        <div>
          <h1>منصة تقارير العمليات</h1>
          <p>
            صفحة واحدة فقط لكتابة ونسخ تقارير العمليات والإشراف. اختر نوع التقرير، يبدأ المؤقت
            تلقائياً، ثم جهز التقرير وانسخه بالنموذج المطلوب.
          </p>
        </div>
        <div class="stats">
          <div class="stat">
            <div class="stat-label">الوقت الحالي في السعودية</div>
            <div class="stat-value" id="riyadhClock">--:--:--</div>
          </div>
          <div class="stat">
            <div class="stat-label">المؤقت الحالي</div>
            <div class="stat-value" id="timerValue">غير نشط</div>
            <div class="stat-label" id="timerStatus">اضغط أحد الأزرار لبدء مؤقت الساعة</div>
          </div>
        </div>
      </section>

      <section class="service-grid" id="serviceButtons">
        <button class="service-btn active" data-service="operations-center" type="button">
          <strong>تقارير مركز العمليات</strong>
          <span>تقرير الاستلام الكامل مع التوجيه الإلكتروني وتسجيل الخروج.</span>
        </button>
        <button class="service-btn" data-service="regions-supervision" type="button">
          <strong>تقارير إشراف ضباط المناطق</strong>
          <span>نموذج استلام ضابط المنطقة مع خيار سري ورتب الصف.</span>
        </button>
        <button class="service-btn" data-service="officers-supervision" type="button">
          <strong>تقارير الإشراف (الضباط)</strong>
          <span>تقرير الضباط بصيغة موسعة مع الرتبة والنداء.</span>
        </button>
        <button class="service-btn" data-service="senior-officers-supervision" type="button">
          <strong>تقارير إشراف كبار الضباط</strong>
          <span>تقرير كبار الضباط مع خيارات مدار وحزم ودرع.</span>
        </button>
        <button class="service-btn" data-service="field-direction-writing" type="button">
          <strong>كتابة التوجيه الميداني</strong>
          <span>إضافة كود مع التوجيه المطلوب وخيار سري ونسخ الصيغة الجاهزة.</span>
        </button>
      </section>

      <section class="workspace">
        <div class="panel forms">
          <section id="operations-center" class="active">
            <h2>تقارير مركز العمليات</h2>
            <div class="mini-card">
              <h3>التوجيه الإلكتروني</h3>
              <div class="mini-grid">
                <div>
                  <label for="routeCode">الكود</label>
                  <input id="routeCode" type="text" placeholder="الكود فقط" />
                </div>
                <div>
                  <label for="routeCategory">الفئة</label>
                  <select id="routeCategory">
                    <option>دوريات الأمن العام</option>
                    <option>قيادة</option>
                    <option>درع</option>
                    <option>حزم</option>
                    <option>مدار</option>
                    <option>وحدات تسعين</option>
                    <option>ضباط مناطق</option>
                    <option>وحدات الفرقة التدخل السريع</option>
                    <option>شرطة عسكرية</option>
                    <option>مرور</option>
                    <option>أمن الطرق</option>
                    <option>مكافحة المخدرات</option>
                    <option>مهمات وواجبات خاصة</option>
                    <option>البحث و التحري</option>
                  </select>
                </div>
                <div class="checkbox" style="margin: 0 0 10px 0">
                  <input id="routeSecret" type="checkbox" />
                  <label for="routeSecret" style="margin: 0; color: var(--text)">سري</label>
                </div>
                <button class="btn btn-primary" type="button" id="addRouteBtn">إضافة توجيه</button>
              </div>
              <div class="notice">
                توزيع وسط 1 ثم شرق 1 ثم جنوب 1 ثم شمال 1 ثم غرب 1 ثم يعود إلى وسط 2 يطبق فقط
                على فئة دوريات الأمن العام.
              </div>
              <div class="list" id="routedList"></div>
              <h3 style="margin-top: 18px">قائمة تسجيل الخروج</h3>
              <div class="list" id="exitList"></div>
            </div>

            <div class="fields">
              <div>
                <label for="operationsOfficer">مركز العمليات</label>
                <input id="operationsOfficer" type="text" placeholder="اسم العمليات" />
              </div>
              <div>
                <label for="deputyOfficer">نائب مركز العمليات</label>
                <input id="deputyOfficer" type="text" placeholder="اسم النائب" />
              </div>
              <div>
                <label for="commandLeadership">القيادة</label>
                <input id="commandLeadership" type="text" placeholder="X" />
              </div>
              <div>
                <label for="diraaUnits">وحدات درع</label>
                <input id="diraaUnits" type="text" placeholder="X" />
              </div>
              <div>
                <label for="hazmUnits">وحدات حزم</label>
                <input id="hazmUnits" type="text" placeholder="X" />
              </div>
              <div>
                <label for="rapidIntervention">وحدات الفرقة التدخل السريع</label>
                <input id="rapidIntervention" type="text" placeholder="X" />
              </div>
              <div>
                <label for="madar1">مدار 1</label>
                <input id="madar1" type="text" placeholder="CC X" />
              </div>
              <div>
                <label for="madar2">مدار 2</label>
                <input id="madar2" type="text" placeholder="X" />
              </div>
              <div>
                <label for="madar3">مدار 3</label>
                <input id="madar3" type="text" placeholder="CC X" />
              </div>
              <div>
                <label for="taseen1">تسعين 1</label>
                <input id="taseen1" type="text" placeholder="CC X" />
              </div>
              <div>
                <label for="regionOfficers">ضباط المناطق</label>
                <input id="regionOfficers" type="text" placeholder="ضابط شمال X - ضابط وسط X" />
              </div>
              <div>
                <label for="militaryPolice">شرطة عسكرية 1</label>
                <input id="militaryPolice" type="text" placeholder="X" />
              </div>
              <div>
                <label for="north">شمال</label>
                <input id="north" type="text" placeholder="X" />
              </div>
              <div>
                <label for="center">وسط</label>
                <input id="center" type="text" placeholder="X" />
              </div>
              <div>
                <label for="east">شرق</label>
                <input id="east" type="text" placeholder="X" />
              </div>
              <div>
                <label for="south">جنوب</label>
                <input id="south" type="text" placeholder="X" />
              </div>
              <div>
                <label for="west">غرب</label>
                <input id="west" type="text" placeholder="X" />
              </div>
              <div>
                <label for="saqrUnit">وحدة صقر</label>
                <input id="saqrUnit" type="text" placeholder="X" />
              </div>
              <div>
                <label for="specialMissions">المهمات والواجبات الخاصة</label>
                <input id="specialMissions" type="text" placeholder="X" />
              </div>
              <div>
                <label for="investigation">البحث والتحري</label>
                <input id="investigation" type="text" placeholder="X" />
              </div>
              <div>
                <label for="traffic">المرور</label>
                <input id="traffic" type="text" placeholder="X" />
              </div>
              <div>
                <label for="roadSecurity">أمن الطرق</label>
                <input id="roadSecurity" type="text" placeholder="X" />
              </div>
              <div>
                <label for="narcotics">مكافحة المخدرات</label>
                <input id="narcotics" type="text" placeholder="X" />
              </div>
              <div class="full">
                <label for="jointUnits">الوحدات المشتركة</label>
                <input id="jointUnits" type="text" placeholder="X" />
              </div>
            </div>

            <div class="action-row">
              <button class="btn btn-primary" type="button" id="copyOperations">نسخ التقرير</button>
              <button class="btn btn-danger" type="button" id="resetOperations">إعادة تعيين التقرير</button>
            </div>
          </section>

          <section id="regions-supervision">
            <h2>تقارير إشراف ضباط المناطق</h2>
            <div class="fields">
              <div>
                <label for="regionAssignment">توجيهك الحالي</label>
                <select id="regionAssignment">
                  <option>ضابط شمال</option>
                  <option selected>ضابط وسط</option>
                  <option>ضابط شرق</option>
                  <option>ضابط غرب</option>
                  <option>ضابط جنوب</option>
                </select>
              </div>
              <div>
                <label for="regionNumber">الرقم</label>
                <input id="regionNumber" type="number" min="1" value="1" />
              </div>
              <div>
                <label for="regionRank">الرتبة</label>
                <select id="regionRank">
                  <option>وكيل رقيب</option>
                  <option>رقيب</option>
                  <option>رقيب أول</option>
                  <option>رئيس رقباء</option>
                </select>
              </div>
              <div>
                <label for="regionWriter">رافع التقرير</label>
                <input id="regionWriter" type="text" placeholder="اسمك" />
              </div>
              <div class="full checkbox">
                <input id="regionSecret" type="checkbox" />
                <label for="regionSecret" style="margin: 0; color: var(--text)">تفعيل وضع سري</label>
              </div>
              <div>
                <label for="regionOperationsOfficer">اسم العمليات والكود العسكري</label>
                <input id="regionOperationsOfficer" type="text" placeholder="الاسم + الكود" />
              </div>
              <div>
                <label for="regionDeputyOfficer">اسم النائب والكود العسكري</label>
                <input id="regionDeputyOfficer" type="text" placeholder="الاسم + الكود" />
              </div>
              <div class="full">
                <label for="regionActiveUnits">الوحدات المفعلة</label>
                <input id="regionActiveUnits" type="text" value="الــدوريــات الأمــنــيــة" />
              </div>
              <div>
                <label for="regionPositive">ملاحظات إيجابية</label>
                <textarea id="regionPositive">لا يوجد</textarea>
              </div>
              <div>
                <label for="regionNegative">ملاحظات سلبية</label>
                <textarea id="regionNegative">لا يوجد</textarea>
              </div>
            </div>
            <div class="action-row">
              <button class="btn btn-primary" type="button" id="copyRegions">نسخ التقرير</button>
              <button class="btn btn-danger" type="button" id="resetRegions">إعادة تعيين التقرير</button>
            </div>
          </section>

          <section id="officers-supervision">
            <h2>تقارير الإشراف (الضباط)</h2>
            <div class="fields">
              <div>
                <label for="officerAssignment">التوجيه</label>
                <select id="officerAssignment">
                  <option>ضابط شمال</option>
                  <option selected>ضابط وسط</option>
                  <option>ضابط شرق</option>
                  <option>ضابط غرب</option>
                  <option>ضابط جنوب</option>
                  <option>تسعين</option>
                </select>
              </div>
              <div>
                <label for="officerNumber">الرقم</label>
                <input id="officerNumber" type="number" min="1" value="1" />
              </div>
              <div>
                <label for="officerRank">الرتبة</label>
                <select id="officerRank">
                  <option>ملازم</option>
                  <option>ملازم أول</option>
                  <option>نقيب</option>
                </select>
              </div>
              <div>
                <label for="officerWriter">كاتب ومقدم التقرير</label>
                <input id="officerWriter" type="text" placeholder="الاسم" />
              </div>
              <div class="full checkbox">
                <input id="officerSecret" type="checkbox" />
                <label for="officerSecret" style="margin: 0; color: var(--text)">تفعيل وضع سري</label>
              </div>
              <div>
                <label for="officerCallSign">النداء</label>
                <input id="officerCallSign" type="text" placeholder="الكود أو النداء" />
              </div>
              <div>
                <label for="officerOperationsOfficer">مركز العمليات الأمن العام</label>
                <input id="officerOperationsOfficer" type="text" placeholder="الاسم" />
              </div>
              <div>
                <label for="officerDeputyOfficer">نائب مركز العمليات الأمن العام</label>
                <input id="officerDeputyOfficer" type="text" placeholder="الاسم" />
              </div>
              <div>
                <label for="officerEvents">الأحداث</label>
                <textarea id="officerEvents">X</textarea>
              </div>
              <div>
                <label for="officerActiveUnits">الدورات المفعلة</label>
                <textarea id="officerActiveUnits">X</textarea>
              </div>
              <div>
                <label for="officerPositive">الملاحظات الإيجابية</label>
                <textarea id="officerPositive">X</textarea>
              </div>
              <div>
                <label for="officerNegative">الملاحظات السلبية</label>
                <textarea id="officerNegative">X</textarea>
              </div>
            </div>
            <div class="action-row">
              <button class="btn btn-primary" type="button" id="copyOfficers">نسخ التقرير</button>
              <button class="btn btn-danger" type="button" id="resetOfficers">إعادة تعيين التقرير</button>
            </div>
          </section>

          <section id="senior-officers-supervision">
            <h2>تقارير إشراف كبار الضباط</h2>
            <div class="fields">
              <div>
                <label for="seniorAssignment">التوجيه</label>
                <select id="seniorAssignment">
                  <option>مدار</option>
                  <option>حزم</option>
                  <option>درع</option>
                </select>
              </div>
              <div>
                <label for="seniorNumber">الرقم</label>
                <input id="seniorNumber" type="number" min="1" value="1" />
              </div>
              <div>
                <label for="seniorRank">الرتبة</label>
                <select id="seniorRank">
                  <option>رائد</option>
                  <option>رائد ركن</option>
                  <option>مقدم</option>
                  <option>مقدم ركن</option>
                  <option>عقيد</option>
                  <option>عقيد ركن</option>
                  <option>عميد</option>
                  <option>عميد ركن</option>
                  <option>لواء</option>
                  <option>لواء ركن</option>
                </select>
              </div>
              <div>
                <label for="seniorWriter">كاتب ومقدم التقرير</label>
                <input id="seniorWriter" type="text" placeholder="الاسم" />
              </div>
              <div>
                <label for="seniorCallSign">النداء</label>
                <input id="seniorCallSign" type="text" placeholder="الكود أو النداء" />
              </div>
              <div>
                <label for="seniorOperationsOfficer">مركز العمليات الأمن العام</label>
                <input id="seniorOperationsOfficer" type="text" placeholder="الاسم" />
              </div>
              <div>
                <label for="seniorDeputyOfficer">نائب العمليات الأمن العام</label>
                <input id="seniorDeputyOfficer" type="text" placeholder="الاسم" />
              </div>
              <div>
                <label for="seniorEvents">الأحداث</label>
                <textarea id="seniorEvents">X</textarea>
              </div>
              <div>
                <label for="seniorActiveUnits">الدورات المفعلة</label>
                <textarea id="seniorActiveUnits">X</textarea>
              </div>
            </div>
            <div class="action-row">
              <button class="btn btn-primary" type="button" id="copySenior">نسخ التقرير</button>
              <button class="btn btn-danger" type="button" id="resetSenior">إعادة تعيين التقرير</button>
            </div>
          </section>

          <section id="field-direction-writing">
            <h2>كتابة التوجيه الميداني</h2>
            <div class="fields">
              <div>
                <label for="fieldDirectionCode">الكود</label>
                <input id="fieldDirectionCode" type="text" placeholder="P-123" />
              </div>
              <div>
                <label for="fieldDirectionTarget">التوجيه</label>
                <select id="fieldDirectionTarget">
                  <optgroup label="القطاع الأمن العام">
                    <option>وسط</option>
                    <option>شرق</option>
                    <option>جنوب</option>
                    <option>شمال</option>
                    <option>غرب</option>
                    <option>ضابط وسط</option>
                    <option>ضابط شرق</option>
                    <option>ضابط جنوب</option>
                    <option>ضابط شمال</option>
                    <option>ضابط غرب</option>
                  </optgroup>
                  <optgroup label="القطاع المرور">
                    <option>ساهر</option>
                    <option>سير</option>
                    <option>رصد</option>
                    <option>ميم</option>
                  </optgroup>
                  <optgroup label="القطاع أمن طرق">
                    <option>ضبط 1</option>
                    <option>ضبط 2</option>
                    <option>ضبط 3</option>
                    <option>عين 1</option>
                    <option>عين 2</option>
                    <option>عين 3</option>
                    <option>أمن 1</option>
                    <option>أمن 2</option>
                    <option>أمن 3</option>
                    <option>رصد</option>
                  </optgroup>
                  <optgroup label="القطاع أمن المحافظات مهمات و واجبات خاصة">
                    <option>شهاب 1</option>
                    <option>شهاب 2</option>
                    <option>برق 1</option>
                    <option>برق 2</option>
                    <option>برق 3</option>
                    <option>مهام 1</option>
                    <option>مهام 2</option>
                    <option>مهام 3</option>
                  </optgroup>
                  <optgroup label="القطاع مكافحة المخدرات">
                    <option>مكافحة</option>
                    <option>سيف</option>
                    <option>ميم كاف 1</option>
                    <option>ميم كاف 2</option>
                    <option>ميم كاف 3</option>
                    <option>ميم كاف 4</option>
                    <option>ميم كاف 5</option>
                    <option>رصد</option>
                  </optgroup>
                  <optgroup label="البحث و التحري">
                    <option>بحث وتحري 1</option>
                    <option>بحث وتحري 2</option>
                  </optgroup>
                </select>
              </div>
              <div class="checkbox" style="margin-top: 34px">
                <input id="fieldDirectionSecret" type="checkbox" />
                <label for="fieldDirectionSecret" style="margin: 0; color: var(--text)">سري</label>
              </div>
            </div>
            <div class="action-row">
              <button class="btn btn-primary" type="button" id="addFieldDirection">إضافة التوجيه</button>
              <button class="btn btn-secondary" type="button" id="copyFieldDirections">نسخ التوجيه</button>
              <button class="btn btn-danger" type="button" id="resetFieldDirections">إعادة تعيين</button>
            </div>
            <div class="list" id="fieldDirectionsList"></div>
          </section>
        </div>

        <aside class="panel" id="previewPanel">
          <h2>معاينة التقرير</h2>
          <div class="preview-box" id="previewBox"></div>
        </aside>
      </section>
    </div>

    <script>
      const state = {
        activeService: "operations-center",
        sessions: {
          "operations-center": null,
          "regions-supervision": null,
          "officers-supervision": null,
          "senior-officers-supervision": null,
          "field-direction-writing": null,
        },
        routedMembers: [],
        exitMembers: [],
        fieldDirections: [],
        routeIndex: 0,
        routeCounts: {
          "وسط": 0,
          "شرق": 0,
          "جنوب": 0,
          "شمال": 0,
          "غرب": 0,
        },
      };

      const routeCycle = ["وسط", "شرق", "جنوب", "شمال", "غرب"];

      function byId(id) {
        return document.getElementById(id);
      }

      function value(id) {
        return byId(id).value.trim();
      }

      function formatTime(date, withSeconds = false) {
        return new Intl.DateTimeFormat("ar-SA-u-nu-latn", {
          timeZone: "Asia/Riyadh",
          hour: "numeric",
          minute: "2-digit",
          second: withSeconds ? "2-digit" : undefined,
          hour12: true,
        }).format(date);
      }

      function formatDate(date) {
        return new Intl.DateTimeFormat("ar-SA-u-nu-latn", {
          timeZone: "Asia/Riyadh",
          year: "numeric",
          month: "numeric",
          day: "numeric",
        }).format(date);
      }

      function activeStartDate() {
        const start = state.sessions[state.activeService];
        return start ? new Date(start) : new Date();
      }

      function activeEndDate() {
        const start = state.sessions[state.activeService];
        if (!start) return new Date();
        const end = start + 60 * 60 * 1000;
        return new Date(Math.min(Date.now(), end));
      }

      function ensureSession(service) {
        if (!state.sessions[service]) {
          state.sessions[service] = Date.now();
        }
      }

      function updateClockAndTimer() {
        const now = new Date();
        byId("riyadhClock").textContent = formatTime(now, true);

        const start = state.sessions[state.activeService];
        if (!start) {
          byId("timerValue").textContent = "غير نشط";
          byId("timerStatus").textContent = "اضغط أحد الأزرار لبدء مؤقت الساعة";
          byId("timerStatus").className = "stat-label status-idle";
          return;
        }

        const end = start + 60 * 60 * 1000;
        const remaining = end - Date.now();

        if (remaining <= 0) {
          byId("timerValue").textContent = "00:00:00";
          byId("timerStatus").textContent = "تقريرك جاهز";
          byId("timerStatus").className = "stat-label status-ready";
          return;
        }

        const total = Math.floor(remaining / 1000);
        const hours = String(Math.floor(total / 3600)).padStart(2, "0");
        const minutes = String(Math.floor((total % 3600) / 60)).padStart(2, "0");
        const seconds = String(total % 60).padStart(2, "0");

        byId("timerValue").textContent = `${hours}:${minutes}:${seconds}`;
        byId("timerStatus").textContent = `بدأ من ${formatTime(new Date(start))} ويتوقف بعد ساعة كاملة`;
        byId("timerStatus").className = "stat-label";
      }

      function appendValue(manual, extras) {
        const items = [];
        if (manual) items.push(manual);
        if (extras.length) items.push(extras.join(" | "));
        return items.length ? items.join(" | ") : "X";
      }

      function routedByCategory(category) {
        return state.routedMembers.filter((item) => item.category === category);
      }

      function routedByDirection(direction) {
        return state.routedMembers
          .filter((item) => item.category === "دوريات الأمن العام" && item.direction === direction)
          .map((item) => item.summary);
      }

      function categorySummary(category) {
        return routedByCategory(category).map((item) => item.summary);
      }

      function buildOperationsReport() {
        const start = activeStartDate();
        const end = activeEndDate();

        const commandLeadership = appendValue(value("commandLeadership"), categorySummary("قيادة"));
        const diraaUnits = appendValue(value("diraaUnits"), categorySummary("درع"));
        const hazmUnits = appendValue(value("hazmUnits"), categorySummary("حزم"));
        const madarUnits = categorySummary("مدار");
        const madar1 = appendValue(value("madar1"), madarUnits);
        const taseen = appendValue(value("taseen1"), categorySummary("وحدات تسعين"));
        const regionOfficers = appendValue(value("regionOfficers"), categorySummary("ضباط مناطق"));
        const rapidIntervention = appendValue(value("rapidIntervention"), categorySummary("وحدات الفرقة التدخل السريع"));
        const militaryPolice = appendValue(value("militaryPolice"), categorySummary("شرطة عسكرية"));
        const traffic = appendValue(value("traffic"), categorySummary("مرور"));
        const roadSecurity = appendValue(value("roadSecurity"), categorySummary("أمن الطرق"));
        const narcotics = appendValue(value("narcotics"), categorySummary("مكافحة المخدرات"));
        const specialMissions = appendValue(value("specialMissions"), categorySummary("مهمات وواجبات خاصة"));
        const investigation = appendValue(value("investigation"), categorySummary("البحث و التحري"));
        const centerPatrols = appendValue(value("center"), routedByDirection("وسط"));
        const eastPatrols = appendValue(value("east"), routedByDirection("شرق"));
        const southPatrols = appendValue(value("south"), routedByDirection("جنوب"));
        const northPatrols = appendValue(value("north"), routedByDirection("شمال"));
        const westPatrols = appendValue(value("west"), routedByDirection("غرب"));
        const exitSummary = state.exitMembers.length
          ? state.exitMembers.map((item) => item.summary || item.code || "بدون كود").join(" | ")
          : "لا يوجد";

        return [
          `تم استلام مهام نائب العمليات من ${formatTime(start)} الى ${formatTime(end)}`,
          `مركز العمليات : ${value("operationsOfficer") || " "}`,
          `نائب مركز العمليات : ${value("deputyOfficer") || " "}`,
          "—— [  الــقــيــاده  ] ——",
          commandLeadership,
          "—— [ وحدات درع ] ——",
          diraaUnits,
          "—— [ وحدات حزم ] ——",
          hazmUnits,
          "ـــــــــــــــــــــــــــــــــ وحدات الفرقة التدخل السريع ـــــــــــــــــــــــــــــــــ",
          rapidIntervention,
          "— [ وحدات مدار ]——",
          `مدار 1 | ${madar1}`,
          `مدار 2 | ${value("madar2") || "X"}`,
          `مدار 3 | ${value("madar3") || "X"}`,
          "—— [ وحدات تسعين ] ——",
          `تسعين 1 | ${taseen}`,
          "—— [ ضباط المناطق ] ——",
          regionOfficers,
          "—— [ شــرطــة عــســكــريــة ] ——",
          `شرطة عسكرية 1 | ${militaryPolice}`,
          "—— [ شمال ] ——",
          northPatrols,
          "—— [ وسط ] ——",
          centerPatrols,
          "—— [ شرق ] ——",
          eastPatrols,
          "—— [ جنوب ] ——",
          southPatrols,
          "—— [ غرب ] ——",
          westPatrols,
          "—— [ وحــدة صــقــر ] ——",
          value("saqrUnit") || "X",
          "—— [ المهمات و الواجبات الخاصة ] ——",
          specialMissions,
          "—— [ البحث و التحري ] ——",
          investigation,
          "—— [ المرور ] ——",
          traffic,
          "—— [ أمن الطرق ] ——",
          roadSecurity,
          "—— [ مكافحة المخدرات ] ——",
          narcotics,
          "—— [ الــوحدات الــمــشــتــركــة ] ——",
          value("jointUnits") || "X",
          "—— [ تسجيل خروج ] ——",
          exitSummary,
        ].join("\n");
      }

      function buildAssignmentLabel(prefix, number, secret) {
        return `${prefix} ${number}${secret ? " سري" : ""}`.trim();
      }

      function buildRegionsReport() {
        const assignment = buildAssignmentLabel(
          byId("regionAssignment").value,
          value("regionNumber") || "1",
          byId("regionSecret").checked,
        );
        return [
          `تم أستلام مهام ( ${assignment} ) من الساعه ${formatTime(activeStartDate())} الى الساعه ${formatTime(activeEndDate())}`,
          `اسم العمليات والكود العسكري : ${value("regionOperationsOfficer") || " "}`,
          `اسم النائب والكود العسكري : ${value("regionDeputyOfficer") || " "}`,
          `الوحدات المفعلة : ${value("regionActiveUnits") || "الــدوريــات الأمــنــيــة"}`,
          `ملاحظات إيجابية : ${value("regionPositive") || "لا يوجد"}`,
          `ملاحظات سلبية : ${value("regionNegative") || "لا يوجد"}`,
          `تم رفع التقرير من قبل (${byId("regionRank").value}) : ${value("regionWriter") || " "}`,
        ].join("\n");
      }

      function buildOfficersReport() {
        const assignment = buildAssignmentLabel(
          byId("officerAssignment").value,
          value("officerNumber") || "1",
          byId("officerSecret").checked,
        );
        return [
          "﷽",
          "الأمــــــــــــــــــــــــــن الـــــــعــــــــــام بمـــديـــنة الـــ 90",
          `تقرير استلام ( ${assignment} ) من الساعة ( ${formatTime(activeStartDate())} الى الساعة ${formatTime(activeEndDate())} )`,
          `التاريخ : ${formatDate(new Date())}`,
          `الأحداث : ${value("officerEvents") || "X"}`,
          `الدورات المفعلة : ${value("officerActiveUnits") || "X"}`,
          `الملاحظات الإيجابية : ${value("officerPositive") || "X"}`,
          `الملاحظات السلبية : ${value("officerNegative") || "X"}`,
          `مركز العمليات الأمن العام : ${value("officerOperationsOfficer") || " "}`,
          `نائب مركز العمليات الأمن العام : ${value("officerDeputyOfficer") || " "}`,
          `كاتب ومقدم التقرير : ${value("officerWriter") || " "}`,
          `الرتبة : ${byId("officerRank").value}`,
          `النداء : ${value("officerCallSign") || " "}`,
          "يقدم التقرير الى سعادة قادة الشرطة .. ونوابه الكرام",
        ].join("\n");
      }

      function buildSeniorReport() {
        const assignment = `${byId("seniorAssignment").value} ${value("seniorNumber") || "1"}`.trim();
        return [
          "﷽",
          "الأمــــــــــــــــــــــــــن الـــــــعــــــــــام بمـــديـــنة الـــ 90",
          `تقرير استلام ( ${assignment} ) من الساعة ( ${formatTime(activeStartDate())} الى الساعة ${formatTime(activeEndDate())} )`,
          `التاريخ : ${formatDate(new Date())}`,
          `الأحداث : ${value("seniorEvents") || "X"}`,
          `الدورات المفعلة : ${value("seniorActiveUnits") || "X"}`,
          `مركز العمليات الأمن العام : ${value("seniorOperationsOfficer") || " "}`,
          `نائب العمليات الأمن العام : ${value("seniorDeputyOfficer") || " "}`,
          `كاتب ومقدم التقرير : ${value("seniorWriter") || " "}`,
          `الرتبة : ${byId("seniorRank").value}`,
          `النداء : ${value("seniorCallSign") || " "}`,
          "يقدم التقرير الى سعادة قادة الشرطة .. ونوابه الكرام",
        ].join("\n");
      }

      function buildFieldDirectionText() {
        if (!state.fieldDirections.length) {
          const code = value("fieldDirectionCode");
          const direction = byId("fieldDirectionTarget").value;
          const isSecret = byId("fieldDirectionSecret").checked;
          if (!code) {
            return "";
          }
          return `${direction}${isSecret ? " سري" : ""} | ${code}`;
        }

        return state.fieldDirections.map((item) => item.summary).join("\n");
      }

      function currentReportText() {
        if (state.activeService === "operations-center") return buildOperationsReport();
        if (state.activeService === "regions-supervision") return buildRegionsReport();
        if (state.activeService === "officers-supervision") return buildOfficersReport();
        if (state.activeService === "field-direction-writing") return buildFieldDirectionText();
        return buildSeniorReport();
      }

      function updatePreview() {
        byId("previewBox").textContent = currentReportText();
      }

      function renderLists() {
        const routedList = byId("routedList");
        const exitList = byId("exitList");
        const fieldDirectionsList = byId("fieldDirectionsList");

        if (!state.routedMembers.length) {
          routedList.innerHTML = '<div class="notice">لا يوجد توجيه مضاف حتى الآن.</div>';
        } else {
          routedList.innerHTML = state.routedMembers
            .map(
              (item) => `
                <div class="list-item">
                  <div>
                    <strong>${item.code || "بدون كود"}</strong>
                    <small>${item.summary}</small>
                  </div>
                  <button class="btn btn-secondary" type="button" data-exit-id="${item.id}">تسجيل خروج</button>
                </div>
              `,
            )
            .join("");
        }

        if (!state.exitMembers.length) {
          exitList.innerHTML = '<div class="notice">لا يوجد مسجلين خروج.</div>';
        } else {
          exitList.innerHTML = state.exitMembers
            .map(
              (item) => `
                <div class="list-item">
                  <div>
                    <strong>${item.code || "بدون كود"}</strong>
                    <small>${item.summary || item.code || "بدون كود"}</small>
                  </div>
                </div>
              `,
            )
            .join("");
        }

        if (!fieldDirectionsList) return;

        if (!state.fieldDirections.length) {
          fieldDirectionsList.innerHTML = '<div class="notice">لا يوجد توجيه ميداني مضاف حتى الآن.</div>';
        } else {
          fieldDirectionsList.innerHTML = state.fieldDirections
            .map(
              (item) => `
                <div class="list-item">
                  <div>
                    <strong>${item.code}</strong>
                    <small>${item.summary}</small>
                  </div>
                </div>
              `,
            )
            .join("");
        }
      }

      function addRoute() {
        const code = value("routeCode");
        const category = byId("routeCategory").value;
        const isSecret = byId("routeSecret").checked;

        if (!code) {
          alert("اكتب الكود قبل إضافة التوجيه");
          return;
        }

        const isPublicPatrol = category === "دوريات الأمن العام";
        let direction = "";
        let round = null;
        let label = category;

        if (isPublicPatrol) {
          direction = routeCycle[state.routeIndex % routeCycle.length];
          state.routeIndex += 1;
          state.routeCounts[direction] += 1;
          round = state.routeCounts[direction];
          label = `${direction} ${round}${isSecret ? " سري" : ""}`;
        } else {
          label = `${category}${isSecret ? " سري" : ""}`;
        }

        const member = {
          id: String(Date.now() + Math.random()),
          code,
          category,
          direction,
          round,
          secret: isSecret,
          label,
          summary: `${label} - ${code}`,
        };

        state.routedMembers.push(member);
        byId("routeCode").value = "";
        byId("routeSecret").checked = false;
        renderLists();
        updatePreview();
      }

      function registerExit(id) {
        const memberIndex = state.routedMembers.findIndex((item) => item.id === id);
        if (memberIndex === -1) return;
        const member = state.routedMembers.splice(memberIndex, 1)[0];
        state.exitMembers.push({ id: member.id, name: "", code: member.code, summary: member.summary });
        renderLists();
        updatePreview();
      }

      function addFieldDirection() {
        const code = value("fieldDirectionCode");
        const direction = byId("fieldDirectionTarget").value;
        const isSecret = byId("fieldDirectionSecret").checked;

        if (!code) {
          alert("اكتب الكود قبل إضافة التوجيه الميداني");
          return;
        }

        state.fieldDirections.push({
          id: String(Date.now() + Math.random()),
          code,
          direction,
          secret: isSecret,
          summary: `${direction}${isSecret ? " سري" : ""} | ${code}`,
        });

        byId("fieldDirectionCode").value = "";
        byId("fieldDirectionSecret").checked = false;
        renderLists();
        updatePreview();
      }

      function switchService(service) {
        state.activeService = service;
        ensureSession(service);

        document.querySelectorAll(".service-btn").forEach((button) => {
          button.classList.toggle("active", button.dataset.service === service);
        });

        document.querySelectorAll(".forms > section").forEach((section) => {
          section.classList.toggle("active", section.id === service);
        });

        byId("previewPanel").style.display =
          service === "field-direction-writing" ? "none" : "";

        updateClockAndTimer();
        updatePreview();
      }

      function copyText(text) {
        if (navigator.clipboard && window.isSecureContext) {
          return navigator.clipboard.writeText(text);
        }

        const area = document.createElement("textarea");
        area.value = text;
        document.body.appendChild(area);
        area.select();
        document.execCommand("copy");
        area.remove();
        return Promise.resolve();
      }

      function copyCurrentReport() {
        copyText(currentReportText())
          .then(() => alert("تم نسخ التقرير"))
          .catch(() => alert("تعذر النسخ التلقائي، انسخ النص من المعاينة"));
      }

      function clearInputs(ids) {
        ids.forEach((id) => {
          const element = byId(id);
          if (!element) return;
          if (element.tagName === "SELECT") {
            element.selectedIndex = 0;
          } else if (element.type === "checkbox") {
            element.checked = false;
          } else if (element.tagName === "TEXTAREA") {
            element.value = "";
          } else {
            element.value = "";
          }
        });
      }

      function resetOperations() {
        clearInputs([
          "operationsOfficer",
          "deputyOfficer",
          "commandLeadership",
          "diraaUnits",
          "hazmUnits",
          "rapidIntervention",
          "madar1",
          "madar2",
          "madar3",
          "taseen1",
          "regionOfficers",
          "militaryPolice",
          "north",
          "center",
          "east",
          "south",
          "west",
          "saqrUnit",
          "specialMissions",
          "investigation",
          "traffic",
          "roadSecurity",
          "narcotics",
          "jointUnits",
          "routeCode",
        ]);
        byId("routeCategory").selectedIndex = 0;
        byId("routeSecret").checked = false;
        state.routedMembers = [];
        state.exitMembers = [];
        state.routeIndex = 0;
        state.routeCounts = { "وسط": 0, "شرق": 0, "جنوب": 0, "شمال": 0, "غرب": 0 };
        state.sessions["operations-center"] = null;
        renderLists();
        updateClockAndTimer();
        updatePreview();
      }

      function resetRegions() {
        byId("regionAssignment").selectedIndex = 1;
        byId("regionNumber").value = "1";
        byId("regionRank").selectedIndex = 0;
        byId("regionWriter").value = "";
        byId("regionSecret").checked = false;
        byId("regionOperationsOfficer").value = "";
        byId("regionDeputyOfficer").value = "";
        byId("regionActiveUnits").value = "الــدوريــات الأمــنــيــة";
        byId("regionPositive").value = "لا يوجد";
        byId("regionNegative").value = "لا يوجد";
        state.sessions["regions-supervision"] = null;
        updateClockAndTimer();
        updatePreview();
      }

      function resetOfficers() {
        byId("officerAssignment").selectedIndex = 1;
        byId("officerNumber").value = "1";
        byId("officerRank").selectedIndex = 0;
        byId("officerWriter").value = "";
        byId("officerSecret").checked = false;
        byId("officerCallSign").value = "";
        byId("officerOperationsOfficer").value = "";
        byId("officerDeputyOfficer").value = "";
        byId("officerEvents").value = "X";
        byId("officerActiveUnits").value = "X";
        byId("officerPositive").value = "X";
        byId("officerNegative").value = "X";
        state.sessions["officers-supervision"] = null;
        updateClockAndTimer();
        updatePreview();
      }

      function resetSenior() {
        byId("seniorAssignment").selectedIndex = 0;
        byId("seniorNumber").value = "1";
        byId("seniorRank").selectedIndex = 0;
        byId("seniorWriter").value = "";
        byId("seniorCallSign").value = "";
        byId("seniorOperationsOfficer").value = "";
        byId("seniorDeputyOfficer").value = "";
        byId("seniorEvents").value = "X";
        byId("seniorActiveUnits").value = "X";
        state.sessions["senior-officers-supervision"] = null;
        updateClockAndTimer();
        updatePreview();
      }

      function resetFieldDirections() {
        byId("fieldDirectionCode").value = "";
        byId("fieldDirectionTarget").selectedIndex = 0;
        byId("fieldDirectionSecret").checked = false;
        state.fieldDirections = [];
        state.sessions["field-direction-writing"] = null;
        renderLists();
        updateClockAndTimer();
        updatePreview();
      }

      document.querySelectorAll(".service-btn").forEach((button) => {
        button.addEventListener("click", () => switchService(button.dataset.service));
      });

      byId("addRouteBtn").addEventListener("click", addRoute);
      byId("addFieldDirection").addEventListener("click", addFieldDirection);
      byId("copyOperations").addEventListener("click", copyCurrentReport);
      byId("copyRegions").addEventListener("click", copyCurrentReport);
      byId("copyOfficers").addEventListener("click", copyCurrentReport);
      byId("copySenior").addEventListener("click", copyCurrentReport);
      byId("copyFieldDirections").addEventListener("click", copyCurrentReport);

      byId("resetOperations").addEventListener("click", resetOperations);
      byId("resetRegions").addEventListener("click", resetRegions);
      byId("resetOfficers").addEventListener("click", resetOfficers);
      byId("resetSenior").addEventListener("click", resetSenior);
      byId("resetFieldDirections").addEventListener("click", resetFieldDirections);

      document.body.addEventListener("input", updatePreview);
      document.body.addEventListener("change", updatePreview);

      byId("routedList").addEventListener("click", (event) => {
        const target = event.target.closest("[data-exit-id]");
        if (target) registerExit(target.dataset.exitId);
      });

      renderLists();
      switchService("operations-center");
      updateClockAndTimer();
      updatePreview();
      setInterval(() => {
        updateClockAndTimer();
        updatePreview();
      }, 1000);
    </script>
  </body>
</html>
