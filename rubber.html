import { useState, useMemo } from "react";

const MONTHS_TH = ["ม.ค.", "ก.พ.", "มี.ค.", "เม.ย.", "พ.ค.", "มิ.ย.", "ก.ค.", "ส.ค.", "ก.ย.", "ต.ค.", "พ.ย.", "ธ.ค."];
const MONTHS_FULL = ["มกราคม", "กุมภาพันธ์", "มีนาคม", "เมษายน", "พฤษภาคม", "มิถุนายน", "กรกฎาคม", "สิงหาคม", "กันยายน", "ตุลาคม", "พฤศจิกายน", "ธันวาคม"];

const currentYear = new Date().getFullYear();
const currentMonth = new Date().getMonth() + 1;

const initialTransactions = [
  { id: 1,  date: "2567-11-05", type: "income",  amount: 11000, note: "ขายยางแผ่น", party: "shared" },
  { id: 2,  date: "2567-11-12", type: "expense", amount: 3000,  label: "ค่าปุ๋ย",    party: "shared", note: "" },
  { id: 3,  date: "2567-12-08", type: "income",  amount: 13500, note: "ขายยางถ้วย", party: "shared" },
  { id: 4,  date: "2567-12-20", type: "expense", amount: 900,   label: "ตัดหญ้า",   party: "garden", note: "" },
  { id: 5,  date: "2568-01-10", type: "income",  amount: 10000, note: "ขายยางแผ่น", party: "shared" },
  { id: 6,  date: "2568-01-15", type: "expense", amount: 2000,  label: "น้ำกรด",    party: "shared", note: "" },
  { id: 7,  date: "2568-02-08", type: "income",  amount: 14000, note: "ขายยางแผ่น", party: "shared" },
  { id: 8,  date: "2568-03-05", type: "income",  amount: 9500,  note: "ขายยางถ้วย", party: "shared" },
  { id: 9,  date: "2568-03-18", type: "expense", amount: 5000,  label: "ปุ๋ยเคมี",  party: "shared", note: "" },
  { id: 10, date: "2568-04-22", type: "income",  amount: 12000, note: "ขายยางแผ่น", party: "shared" },
  { id: 11, date: "2568-05-01", type: "income",  amount: 12000, note: "ขายยางแผ่น", party: "shared" },
  { id: 12, date: "2568-05-03", type: "expense", amount: 4000,  label: "ค่าปุ๋ย",   party: "shared", note: "" },
  { id: 13, date: "2568-05-07", type: "expense", amount: 800,   label: "ตัดหญ้า",   party: "garden", note: "" },
  { id: 14, date: "2568-05-10", type: "income",  amount: 9500,  note: "ขายยางถ้วย", party: "shared" },
];

function fmt(n) {
  return Math.abs(n).toLocaleString("th-TH", { minimumFractionDigits: 2, maximumFractionDigits: 2 });
}
function toBE(year) { return year + 543; }
function parseDateParts(dateStr) {
  const [y, m, d] = dateStr.split("-").map(Number);
  return { year: y, month: m, day: d };
}
function computeSummary(txList) {
  let totalIncome = 0, totalExpense = 0;
  let gardenIncome = 0, tapperIncome = 0;
  let gardenExpense = 0, tapperExpense = 0;
  for (const t of txList) {
    if (t.type === "income") {
      totalIncome += t.amount;
      gardenIncome += t.amount * 0.5;
      tapperIncome += t.amount * 0.5;
    } else {
      totalExpense += t.amount;
      if (t.party === "shared") { gardenExpense += t.amount * 0.5; tapperExpense += t.amount * 0.5; }
      else if (t.party === "garden") { gardenExpense += t.amount; }
      else { tapperExpense += t.amount; }
    }
  }
  const gardenNet = gardenIncome - gardenExpense;
  const tapperNet = tapperIncome - tapperExpense;
  return {
    totalIncome, totalExpense,
    gardenIncome, tapperIncome,
    gardenExpense, tapperExpense,
    gardenNet, tapperNet,
    gardenDebt: gardenNet < 0 ? Math.abs(gardenNet) : 0,
    tapperDebt: tapperNet < 0 ? Math.abs(tapperNet) : 0,
  };
}

const inputStyle = {
  width: "100%", border: "2px solid #e0e0e0", borderRadius: 12,
  padding: "14px 14px", fontSize: 18, fontFamily: "Sarabun",
  fontWeight: 600, outline: "none", background: "#fff", boxSizing: "border-box"
};

export default function App() {
  const [view, setView] = useState("dashboard");
  const [mode, setMode] = useState("month"); // "month" | "year" | "all"
  const [selectedYear, setSelectedYear] = useState(toBE(currentYear));
  const [selectedMonth, setSelectedMonth] = useState(currentMonth);
  const [showYearPicker, setShowYearPicker] = useState(false);
  const [showMonthPicker, setShowMonthPicker] = useState(false);
  const [transactions, setTransactions] = useState(initialTransactions);
  const [editingTx, setEditingTx] = useState(null);
  const [form, setForm] = useState({ date: "", amount: "", label: "", party: "", note: "" });

  const allYears = useMemo(() => {
    const ys = [...new Set(transactions.map(t => parseDateParts(t.date).year))];
    if (!ys.includes(selectedYear)) ys.push(selectedYear);
    return ys.sort();
  }, [transactions, selectedYear]);

  const filtered = useMemo(() => {
    return transactions.filter(t => {
      const { year, month } = parseDateParts(t.date);
      if (mode === "all") return true;
      if (mode === "year") return year === selectedYear;
      return year === selectedYear && month === selectedMonth;
    }).sort((a, b) => a.date.localeCompare(b.date));
  }, [transactions, mode, selectedYear, selectedMonth]);

  const summary = useMemo(() => computeSummary(filtered), [filtered]);

  const monthlyBreakdown = useMemo(() => {
    if (mode !== "year") return [];
    const byMonth = {};
    transactions.filter(t => parseDateParts(t.date).year === selectedYear).forEach(t => {
      const { month } = parseDateParts(t.date);
      if (!byMonth[month]) byMonth[month] = [];
      byMonth[month].push(t);
    });
    return Object.entries(byMonth).map(([m, txs]) => ({ month: Number(m), ...computeSummary(txs) })).sort((a, b) => a.month - b.month);
  }, [transactions, mode, selectedYear]);

  const yearlyBreakdown = useMemo(() => {
    if (mode !== "all") return [];
    const byYear = {};
    transactions.forEach(t => {
      const { year } = parseDateParts(t.date);
      if (!byYear[year]) byYear[year] = [];
      byYear[year].push(t);
    });
    return Object.entries(byYear).map(([y, txs]) => ({ year: Number(y), ...computeSummary(txs) })).sort((a, b) => a.year - b.year);
  }, [transactions, mode]);

  function defaultDate() {
    const y = mode === "all" ? toBE(currentYear) : selectedYear;
    const m = mode === "month" ? selectedMonth : currentMonth;
    return `${y}-${String(m).padStart(2, "0")}-${String(new Date().getDate()).padStart(2, "0")}`;
  }

  function openAddIncome() {
    setForm({ date: defaultDate(), amount: "", label: "ขายยาง", party: "shared", note: "" });
    setEditingTx(null); setView("add-income");
  }
  function openAddExpense() {
    setForm({ date: defaultDate(), amount: "", label: "", party: "", note: "" });
    setEditingTx(null); setView("add-expense");
  }
  function openEdit(tx) {
    setForm({ date: tx.date, amount: String(tx.amount), label: tx.label || "ขายยาง", party: tx.party, note: tx.note || "" });
    setEditingTx(tx);
    setView(tx.type === "income" ? "add-income" : "add-expense");
  }
  function saveIncome() {
    if (!form.amount || isNaN(Number(form.amount))) return alert("กรุณาใส่จำนวนเงิน");
    const tx = { id: editingTx ? editingTx.id : Date.now(), date: form.date, type: "income", amount: Number(form.amount), note: form.note, party: "shared" };
    setTransactions(prev => editingTx ? prev.map(t => t.id === editingTx.id ? tx : t) : [...prev, tx]);
    setView("dashboard");
  }
  function saveExpense() {
    if (!form.amount || isNaN(Number(form.amount))) return alert("กรุณาใส่จำนวนเงิน");
    if (!form.party) return alert("กรุณาเลือกว่าใครจ่าย");
    if (!form.label) return alert("กรุณาใส่ชื่อรายการ");
    const tx = { id: editingTx ? editingTx.id : Date.now(), date: form.date, type: "expense", amount: Number(form.amount), label: form.label, party: form.party, note: form.note };
    setTransactions(prev => editingTx ? prev.map(t => t.id === editingTx.id ? tx : t) : [...prev, tx]);
    setView("dashboard");
  }
  function deleteTx(id) {
    if (window.confirm("ลบรายการนี้?")) setTransactions(prev => prev.filter(t => t.id !== id));
  }

  const modeLabel = mode === "month" ? `${MONTHS_FULL[selectedMonth - 1]} ${selectedYear}`
    : mode === "year" ? `ปี ${selectedYear}` : "ทุกปีรวมกัน";

  return (
    <div style={{ fontFamily: "'Sarabun', sans-serif", background: "#f0f4f0", minHeight: "100vh", maxWidth: 480, margin: "0 auto", paddingBottom: 110 }}>
      <link href="https://fonts.googleapis.com/css2?family=Sarabun:wght@400;600;700;800&display=swap" rel="stylesheet" />

      {/* HEADER */}
      <div style={{ background: "linear-gradient(135deg, #2d6a4f 0%, #40916c 100%)", padding: "18px 16px 14px", color: "#fff", position: "sticky", top: 0, zIndex: 100, boxShadow: "0 2px 12px rgba(0,0,0,0.15)" }}>
        <div style={{ display: "flex", alignItems: "center", justifyContent: "space-between", marginBottom: 12 }}>
          <div>
            <div style={{ fontSize: 12, opacity: 0.8, letterSpacing: 1 }}>🌿 สวนยาง 20 ไร่</div>
            <div style={{ fontSize: 20, fontWeight: 800 }}>บัญชีสวนยาง</div>
          </div>
          {(view === "dashboard" || view === "history") && (
            <div style={{ display: "flex", background: "rgba(0,0,0,0.25)", borderRadius: 14, padding: 4, gap: 2 }}>
              {[{ key: "month", label: "เดือน" }, { key: "year", label: "ปี" }, { key: "all", label: "ทั้งหมด" }].map(opt => (
                <button key={opt.key}
                  onClick={() => { setMode(opt.key); setShowYearPicker(false); setShowMonthPicker(false); }}
                  style={{
                    background: mode === opt.key ? "#fff" : "transparent",
                    color: mode === opt.key ? "#2d6a4f" : "rgba(255,255,255,0.85)",
                    border: "none", borderRadius: 10, padding: "8px 13px",
                    fontSize: 14, fontWeight: 800, cursor: "pointer", fontFamily: "Sarabun",
                    transition: "all 0.15s"
                  }}>
                  {opt.label}
                </button>
              ))}
            </div>
          )}
        </div>

        {/* Pickers */}
        {(view === "dashboard" || view === "history") && mode !== "all" && (
          <div style={{ display: "flex", gap: 8 }}>
            <button onClick={() => { setShowYearPicker(!showYearPicker); setShowMonthPicker(false); }}
              style={{ flex: 1, background: "rgba(255,255,255,0.15)", color: "#fff", border: "2px solid rgba(255,255,255,0.35)", borderRadius: 12, padding: "11px 0", fontSize: 16, fontWeight: 800, cursor: "pointer", fontFamily: "Sarabun" }}>
              ปี {selectedYear} {showYearPicker ? "▲" : "▼"}
            </button>
            {mode === "month" && (
              <button onClick={() => { setShowMonthPicker(!showMonthPicker); setShowYearPicker(false); }}
                style={{ flex: 1, background: "rgba(255,255,255,0.15)", color: "#fff", border: "2px solid rgba(255,255,255,0.35)", borderRadius: 12, padding: "11px 0", fontSize: 16, fontWeight: 800, cursor: "pointer", fontFamily: "Sarabun" }}>
                {MONTHS_FULL[selectedMonth - 1]} {showMonthPicker ? "▲" : "▼"}
              </button>
            )}
          </div>
        )}

        {showYearPicker && (
          <div style={{ display: "flex", gap: 8, marginTop: 10 }}>
            {allYears.map(y => (
              <button key={y} onClick={() => { setSelectedYear(y); setShowYearPicker(false); }}
                style={{ flex: 1, padding: "12px 0", borderRadius: 12, border: "none", fontFamily: "Sarabun", fontSize: 17, fontWeight: 700, background: y === selectedYear ? "#fff" : "rgba(255,255,255,0.2)", color: y === selectedYear ? "#2d6a4f" : "#fff", cursor: "pointer" }}>
                {y}
              </button>
            ))}
          </div>
        )}
        {showMonthPicker && (
          <div style={{ display: "grid", gridTemplateColumns: "repeat(4,1fr)", gap: 6, marginTop: 10 }}>
            {MONTHS_TH.map((m, i) => (
              <button key={i} onClick={() => { setSelectedMonth(i + 1); setShowMonthPicker(false); }}
                style={{ padding: "10px 0", borderRadius: 10, border: "none", fontFamily: "Sarabun", fontSize: 15, fontWeight: 700, background: (i + 1) === selectedMonth ? "#fff" : "rgba(255,255,255,0.2)", color: (i + 1) === selectedMonth ? "#2d6a4f" : "#fff", cursor: "pointer" }}>
                {m}
              </button>
            ))}
          </div>
        )}
      </div>

      {/* ===== DASHBOARD ===== */}
      {view === "dashboard" && (
        <div style={{ padding: "16px 14px" }}>

          {/* Big income card */}
          <div style={{ background: "linear-gradient(135deg, #1b4332, #2d6a4f)", borderRadius: 20, padding: "20px 18px", color: "#fff", marginBottom: 14, boxShadow: "0 4px 16px rgba(45,106,79,0.3)" }}>
            <div style={{ fontSize: 14, opacity: 0.85, marginBottom: 2 }}>💰 ยอดขายยางรวม</div>
            <div style={{ fontSize: 42, fontWeight: 800, letterSpacing: -1, lineHeight: 1.1 }}>{fmt(summary.totalIncome)}</div>
            <div style={{ fontSize: 14, opacity: 0.7, marginTop: 2, marginBottom: 14 }}>บาท — {modeLabel}</div>
            <div style={{ display: "flex", gap: 10 }}>
              <div style={{ flex: 1, background: "rgba(255,255,255,0.1)", borderRadius: 12, padding: "10px 12px" }}>
                <div style={{ fontSize: 12, opacity: 0.8 }}>รายจ่ายรวม</div>
                <div style={{ fontSize: 20, fontWeight: 800 }}>-{fmt(summary.totalExpense)}</div>
              </div>
              <div style={{ flex: 1, background: "rgba(255,255,255,0.1)", borderRadius: 12, padding: "10px 12px" }}>
                <div style={{ fontSize: 12, opacity: 0.8 }}>กำไรรวม</div>
                <div style={{ fontSize: 20, fontWeight: 800, color: (summary.totalIncome - summary.totalExpense) >= 0 ? "#b7e4c7" : "#ffb3b3" }}>
                  {(summary.totalIncome - summary.totalExpense) >= 0 ? "+" : "-"}{fmt(Math.abs(summary.totalIncome - summary.totalExpense))}
                </div>
              </div>
            </div>
          </div>

          {/* Side cards */}
          <div style={{ display: "grid", gridTemplateColumns: "1fr 1fr", gap: 10, marginBottom: 14 }}>
            <SideCard emoji="🏡" label="ฝั่งสวน" accent="#2d6a4f" light="#f0f7f4" border="#40916c"
              income={summary.gardenIncome} expense={summary.gardenExpense} net={summary.gardenNet} debt={summary.gardenDebt} />
            <SideCard emoji="🔪" label="ฝั่งคนตัด" accent="#1a759f" light="#e8f4f8" border="#1a759f"
              income={summary.tapperIncome} expense={summary.tapperExpense} net={summary.tapperNet} debt={summary.tapperDebt} />
          </div>

          {/* Debt warning */}
          {(summary.gardenDebt > 0 || summary.tapperDebt > 0) && (
            <div style={{ background: "#fff8f0", border: "2px solid #f4a261", borderRadius: 16, padding: "14px 16px", marginBottom: 14 }}>
              <div style={{ fontSize: 16, fontWeight: 800, color: "#c05621", marginBottom: 10 }}>⚠️ หนี้สะสม — {modeLabel}</div>
              {summary.gardenDebt > 0 && (
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", padding: "8px 0", borderBottom: summary.tapperDebt > 0 ? "1px dashed #f4c09f" : "none" }}>
                  <span style={{ fontSize: 15 }}>🏡 ฝั่งสวนติดหนี้</span>
                  <span style={{ fontSize: 20, fontWeight: 800, color: "#c0392b" }}>{fmt(summary.gardenDebt)} บ.</span>
                </div>
              )}
              {summary.tapperDebt > 0 && (
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", padding: "8px 0" }}>
                  <span style={{ fontSize: 15 }}>🔪 คนตัดติดหนี้</span>
                  <span style={{ fontSize: 20, fontWeight: 800, color: "#c0392b" }}>{fmt(summary.tapperDebt)} บ.</span>
                </div>
              )}
            </div>
          )}

          {/* Monthly breakdown (year mode) */}
          {mode === "year" && monthlyBreakdown.length > 0 && (
            <div style={{ background: "#fff", borderRadius: 16, padding: "14px", marginBottom: 14, boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
              <div style={{ fontSize: 16, fontWeight: 800, color: "#1b4332", marginBottom: 10 }}>📅 สรุปรายเดือน — ปี {selectedYear}</div>
              <div style={{ display: "grid", gridTemplateColumns: "40px 1fr 1fr 1fr", gap: 0 }}>
                <div style={{ fontSize: 12, color: "#aaa", padding: "4px 0", fontWeight: 700 }}></div>
                <div style={{ fontSize: 12, color: "#2d6a4f", padding: "4px 4px", fontWeight: 700, textAlign: "right" }}>รายได้</div>
                <div style={{ fontSize: 12, color: "#c0392b", padding: "4px 4px", fontWeight: 700, textAlign: "right" }}>รายจ่าย</div>
                <div style={{ fontSize: 12, color: "#555", padding: "4px 4px", fontWeight: 700, textAlign: "right" }}>กำไร</div>
              </div>
              {monthlyBreakdown.map(row => {
                const net = row.gardenNet + row.tapperNet;
                return (
                  <div key={row.month} style={{ display: "grid", gridTemplateColumns: "40px 1fr 1fr 1fr", gap: 0, padding: "9px 0", borderTop: "1px solid #f0f0f0", alignItems: "center" }}>
                    <div style={{ fontSize: 15, fontWeight: 800, color: "#333" }}>{MONTHS_TH[row.month - 1]}</div>
                    <div style={{ fontSize: 13, color: "#2d6a4f", fontWeight: 700, textAlign: "right" }}>{fmt(row.totalIncome)}</div>
                    <div style={{ fontSize: 13, color: "#c0392b", fontWeight: 700, textAlign: "right" }}>{fmt(row.totalExpense)}</div>
                    <div style={{ fontSize: 14, fontWeight: 800, color: net >= 0 ? "#2d6a4f" : "#c0392b", textAlign: "right" }}>{net >= 0 ? "+" : "-"}{fmt(Math.abs(net))}</div>
                  </div>
                );
              })}
            </div>
          )}

          {/* Yearly breakdown (all mode) */}
          {mode === "all" && yearlyBreakdown.length > 0 && (
            <div style={{ background: "#fff", borderRadius: 16, padding: "14px", marginBottom: 14, boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
              <div style={{ fontSize: 16, fontWeight: 800, color: "#1b4332", marginBottom: 10 }}>📆 สรุปแยกรายปี</div>
              {yearlyBreakdown.map(row => {
                const net = row.gardenNet + row.tapperNet;
                const totalDebt = row.gardenDebt + row.tapperDebt;
                return (
                  <div key={row.year} style={{ padding: "12px 0", borderTop: "1px solid #f0f0f0" }}>
                    <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 6 }}>
                      <div style={{ fontSize: 18, fontWeight: 800, color: "#1b4332" }}>ปี {row.year}</div>
                      <div style={{ fontSize: 20, fontWeight: 800, color: net >= 0 ? "#2d6a4f" : "#c0392b" }}>
                        {net >= 0 ? "+" : "-"}{fmt(Math.abs(net))} บ.
                      </div>
                    </div>
                    <div style={{ display: "flex", gap: 10, flexWrap: "wrap" }}>
                      <span style={{ fontSize: 13, color: "#2d6a4f", background: "#e8f5e9", borderRadius: 8, padding: "3px 8px" }}>รายได้ {fmt(row.totalIncome)}</span>
                      <span style={{ fontSize: 13, color: "#c0392b", background: "#fce4ec", borderRadius: 8, padding: "3px 8px" }}>รายจ่าย {fmt(row.totalExpense)}</span>
                      {totalDebt > 0 && <span style={{ fontSize: 13, color: "#c05621", background: "#fff3e0", borderRadius: 8, padding: "3px 8px", fontWeight: 700 }}>⚠️ หนี้ {fmt(totalDebt)}</span>}
                    </div>
                  </div>
                );
              })}
            </div>
          )}

          {/* Recent list */}
          <div style={{ background: "#fff", borderRadius: 16, padding: "14px", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
            <div style={{ display: "flex", justifyContent: "space-between", alignItems: "center", marginBottom: 10 }}>
              <div style={{ fontSize: 16, fontWeight: 800, color: "#1b4332" }}>📋 รายการล่าสุด</div>
              <button onClick={() => setView("history")} style={{ background: "none", border: "none", color: "#40916c", fontSize: 14, fontWeight: 700, cursor: "pointer", padding: "4px 8px", fontFamily: "Sarabun" }}>ดูทั้งหมด →</button>
            </div>
            {filtered.length === 0 && <div style={{ textAlign: "center", color: "#aaa", padding: 20, fontSize: 15 }}>ยังไม่มีรายการ</div>}
            {filtered.slice(-6).reverse().map(tx => (
              <TxRow key={tx.id} tx={tx} onEdit={() => openEdit(tx)} onDelete={() => deleteTx(tx.id)} />
            ))}
          </div>
        </div>
      )}

      {/* ===== ADD INCOME ===== */}
      {view === "add-income" && (
        <FormView title={editingTx ? "✏️ แก้ไขรายได้" : "💰 เพิ่มรายได้จากขายยาง"} onBack={() => setView("dashboard")} onSave={saveIncome}>
          <FormField label="วันที่">
            <input type="date" value={form.date} onChange={e => setForm(f => ({ ...f, date: e.target.value }))} style={inputStyle} />
          </FormField>
          <FormField label="ยอดขายยาง (บาท)">
            <input type="number" value={form.amount} onChange={e => setForm(f => ({ ...f, amount: e.target.value }))} placeholder="0.00" inputMode="decimal" style={{ ...inputStyle, fontSize: 30, fontWeight: 800, color: "#2d6a4f" }} />
          </FormField>
          {form.amount && !isNaN(Number(form.amount)) && Number(form.amount) > 0 && (
            <div style={{ background: "#e8f5e9", borderRadius: 14, padding: 16 }}>
              <div style={{ fontSize: 14, color: "#555", marginBottom: 8, fontWeight: 700 }}>แบ่งอัตโนมัติ 50/50 🤝</div>
              <div style={{ display: "flex", justifyContent: "space-between" }}>
                <div><div style={{ fontSize: 12, color: "#888" }}>🏡 ฝั่งสวนได้</div><div style={{ fontSize: 22, fontWeight: 800, color: "#2d6a4f" }}>{fmt(Number(form.amount) / 2)} บ.</div></div>
                <div style={{ textAlign: "right" }}><div style={{ fontSize: 12, color: "#888" }}>🔪 คนตัดได้</div><div style={{ fontSize: 22, fontWeight: 800, color: "#1a759f" }}>{fmt(Number(form.amount) / 2)} บ.</div></div>
              </div>
            </div>
          )}
          <FormField label="หมายเหตุ (ไม่บังคับ)">
            <input type="text" value={form.note} onChange={e => setForm(f => ({ ...f, note: e.target.value }))} placeholder="เช่น ยางแผ่น, ยางถ้วย..." style={inputStyle} />
          </FormField>
        </FormView>
      )}

      {/* ===== ADD EXPENSE ===== */}
      {view === "add-expense" && (
        <FormView title={editingTx ? "✏️ แก้ไขค่าใช้จ่าย" : "💸 เพิ่มค่าใช้จ่าย"} onBack={() => setView("dashboard")} onSave={saveExpense}>
          <FormField label="วันที่">
            <input type="date" value={form.date} onChange={e => setForm(f => ({ ...f, date: e.target.value }))} style={inputStyle} />
          </FormField>
          <FormField label="ชื่อรายการ">
            <input type="text" value={form.label} onChange={e => setForm(f => ({ ...f, label: e.target.value }))} placeholder="เช่น ปุ๋ย ค่าไฟ ตัดหญ้า..." style={inputStyle} />
          </FormField>
          <FormField label="จำนวนเงิน (บาท)">
            <input type="number" value={form.amount} onChange={e => setForm(f => ({ ...f, amount: e.target.value }))} placeholder="0.00" inputMode="decimal" style={{ ...inputStyle, fontSize: 30, fontWeight: 800, color: "#c0392b" }} />
          </FormField>
          <FormField label="ใครจ่าย?">
            <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
              {[
                { key: "shared", emoji: "🤝", label: "จ่ายร่วมกัน", desc: "หาร 50/50 — เช่น ปุ๋ย น้ำกรด ค่าไฟ", color: "#7b2d8b", light: "#f5e8f9" },
                { key: "garden", emoji: "🏡", label: "ฝั่งสวนจ่าย", desc: "เช่น ตัดหญ้า บ้านพัก ซ่อมสวน", color: "#2d6a4f", light: "#e8f5e9" },
                { key: "tapper", emoji: "🔪", label: "ฝั่งคนตัดจ่าย", desc: "ค่าใช้จ่ายของคนตัดยาง", color: "#1a759f", light: "#e3f2fd" },
              ].map(opt => (
                <button key={opt.key} onClick={() => setForm(f => ({ ...f, party: opt.key }))}
                  style={{ background: form.party === opt.key ? opt.light : "#f8f8f8", border: `2px solid ${form.party === opt.key ? opt.color : "#e0e0e0"}`, borderRadius: 14, padding: "14px 16px", textAlign: "left", cursor: "pointer", display: "flex", alignItems: "center", gap: 12 }}>
                  <span style={{ fontSize: 26 }}>{opt.emoji}</span>
                  <div>
                    <div style={{ fontSize: 16, fontWeight: 800, color: form.party === opt.key ? opt.color : "#333", fontFamily: "Sarabun" }}>{opt.label}</div>
                    <div style={{ fontSize: 13, color: "#888", fontFamily: "Sarabun" }}>{opt.desc}</div>
                  </div>
                  {form.party === opt.key && <span style={{ marginLeft: "auto", fontSize: 22, color: opt.color }}>✓</span>}
                </button>
              ))}
            </div>
          </FormField>
          {form.amount && form.party && !isNaN(Number(form.amount)) && Number(form.amount) > 0 && (
            <div style={{ background: "#fff3f3", borderRadius: 12, padding: 14, border: "1px solid #ffcdd2" }}>
              <div style={{ fontSize: 14, color: "#555", marginBottom: 6, fontWeight: 700 }}>ผลที่จะเกิดขึ้น</div>
              {form.party === "shared" && (
                <div style={{ display: "flex", justifyContent: "space-between" }}>
                  <div><div style={{ fontSize: 12, color: "#888" }}>🏡 ฝั่งสวนจ่าย</div><div style={{ fontSize: 20, fontWeight: 800, color: "#c0392b" }}>{fmt(Number(form.amount) / 2)} บ.</div></div>
                  <div style={{ textAlign: "right" }}><div style={{ fontSize: 12, color: "#888" }}>🔪 คนตัดจ่าย</div><div style={{ fontSize: 20, fontWeight: 800, color: "#c0392b" }}>{fmt(Number(form.amount) / 2)} บ.</div></div>
                </div>
              )}
              {form.party === "garden" && <div style={{ fontSize: 17, color: "#c0392b", fontWeight: 800 }}>🏡 ฝั่งสวนจ่ายทั้งหมด {fmt(Number(form.amount))} บ.</div>}
              {form.party === "tapper" && <div style={{ fontSize: 17, color: "#c0392b", fontWeight: 800 }}>🔪 คนตัดจ่ายทั้งหมด {fmt(Number(form.amount))} บ.</div>}
            </div>
          )}
          <FormField label="หมายเหตุ (ไม่บังคับ)">
            <input type="text" value={form.note} onChange={e => setForm(f => ({ ...f, note: e.target.value }))} placeholder="หมายเหตุเพิ่มเติม..." style={inputStyle} />
          </FormField>
        </FormView>
      )}

      {/* ===== HISTORY ===== */}
      {view === "history" && (
        <div style={{ padding: "14px 14px" }}>
          <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 14 }}>
            <button onClick={() => setView("dashboard")} style={{ background: "#2d6a4f", color: "#fff", border: "none", borderRadius: 12, padding: "10px 16px", fontSize: 16, cursor: "pointer", fontFamily: "Sarabun", fontWeight: 700 }}>← กลับ</button>
            <div style={{ fontSize: 17, fontWeight: 800, color: "#1b4332" }}>ประวัติ — {modeLabel}</div>
          </div>
          <div style={{ background: "#fff", borderRadius: 16, padding: 14, overflowX: "auto", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
            <table style={{ width: "100%", borderCollapse: "collapse", fontSize: 13 }}>
              <thead>
                <tr style={{ background: "#f0f7f4" }}>
                  {["วันที่", "รายการ", "ประเภท", "รวม", "ฝั่งสวน", "คนตัด", ""].map((h, i) => (
                    <th key={i} style={{ padding: "9px 6px", textAlign: "left", color: "#2d6a4f", fontFamily: "Sarabun", fontWeight: 700, borderBottom: "2px solid #e0e0e0", whiteSpace: "nowrap" }}>{h}</th>
                  ))}
                </tr>
              </thead>
              <tbody>
                {filtered.length === 0 && <tr><td colSpan={7} style={{ textAlign: "center", padding: 24, color: "#aaa" }}>ไม่มีรายการ</td></tr>}
                {filtered.slice().reverse().map((tx, i) => {
                  const { day, month, year } = parseDateParts(tx.date);
                  const isIncome = tx.type === "income";
                  let gardenAmt = 0, tapperAmt = 0;
                  if (isIncome) { gardenAmt = tx.amount / 2; tapperAmt = tx.amount / 2; }
                  else if (tx.party === "shared") { gardenAmt = -(tx.amount / 2); tapperAmt = -(tx.amount / 2); }
                  else if (tx.party === "garden") { gardenAmt = -tx.amount; }
                  else { tapperAmt = -tx.amount; }
                  return (
                    <tr key={tx.id} style={{ background: i % 2 === 0 ? "#fff" : "#f9fafb", borderBottom: "1px solid #f0f0f0" }}>
                      <td style={{ padding: "8px 5px", whiteSpace: "nowrap", fontSize: 12 }}>{day}/{month}/{String(year).slice(-2)}</td>
                      <td style={{ padding: "8px 5px", maxWidth: 80, overflow: "hidden", textOverflow: "ellipsis", whiteSpace: "nowrap" }}>{tx.label || tx.note || "ขายยาง"}</td>
                      <td style={{ padding: "8px 5px" }}>
                        <span style={{ background: isIncome ? "#e8f5e9" : "#fce4ec", color: isIncome ? "#2d6a4f" : "#c0392b", borderRadius: 6, padding: "2px 5px", fontSize: 11, fontWeight: 700, whiteSpace: "nowrap" }}>
                          {isIncome ? "รายได้" : tx.party === "shared" ? "ร่วม" : tx.party === "garden" ? "สวน" : "ตัด"}
                        </span>
                      </td>
                      <td style={{ padding: "8px 5px", fontWeight: 700, color: isIncome ? "#2d6a4f" : "#c0392b", whiteSpace: "nowrap" }}>{isIncome ? "+" : "-"}{fmt(tx.amount)}</td>
                      <td style={{ padding: "8px 5px", color: gardenAmt >= 0 ? "#2d6a4f" : "#c0392b", fontWeight: 600, whiteSpace: "nowrap" }}>{gardenAmt >= 0 ? "+" : ""}{fmt(Math.abs(gardenAmt))}</td>
                      <td style={{ padding: "8px 5px", color: tapperAmt >= 0 ? "#1a759f" : "#c0392b", fontWeight: 600, whiteSpace: "nowrap" }}>{tapperAmt >= 0 ? "+" : ""}{fmt(Math.abs(tapperAmt))}</td>
                      <td style={{ padding: "8px 5px", whiteSpace: "nowrap" }}>
                        <button onClick={() => openEdit(tx)} style={{ background: "none", border: "none", cursor: "pointer", fontSize: 15 }}>✏️</button>
                        <button onClick={() => deleteTx(tx.id)} style={{ background: "none", border: "none", cursor: "pointer", fontSize: 15 }}>🗑️</button>
                      </td>
                    </tr>
                  );
                })}
              </tbody>
              <tfoot>
                <tr style={{ background: "#f0f7f4", fontWeight: 800 }}>
                  <td colSpan={3} style={{ padding: "10px 6px", color: "#1b4332", fontFamily: "Sarabun" }}>รวม</td>
                  <td style={{ padding: "10px 6px", color: "#2d6a4f", fontFamily: "Sarabun" }}>+{fmt(summary.totalIncome)}</td>
                  <td style={{ padding: "10px 6px", color: summary.gardenNet >= 0 ? "#2d6a4f" : "#c0392b", fontFamily: "Sarabun" }}>{summary.gardenNet >= 0 ? "+" : ""}{fmt(Math.abs(summary.gardenNet))}</td>
                  <td style={{ padding: "10px 6px", color: summary.tapperNet >= 0 ? "#1a759f" : "#c0392b", fontFamily: "Sarabun" }}>{summary.tapperNet >= 0 ? "+" : ""}{fmt(Math.abs(summary.tapperNet))}</td>
                  <td></td>
                </tr>
              </tfoot>
            </table>
          </div>
        </div>
      )}

      {/* BOTTOM BUTTONS */}
      {(view === "dashboard" || view === "history") && (
        <div style={{ position: "fixed", bottom: 0, left: "50%", transform: "translateX(-50%)", width: "100%", maxWidth: 480, background: "#fff", borderTop: "1px solid #e0e0e0", padding: "12px 14px", display: "flex", gap: 10, zIndex: 200, boxShadow: "0 -2px 12px rgba(0,0,0,0.08)" }}>
          <button onClick={openAddIncome}
            style={{ flex: 1, background: "linear-gradient(135deg, #2d6a4f, #52b788)", color: "#fff", border: "none", borderRadius: 16, padding: "16px 8px", fontSize: 16, fontWeight: 800, cursor: "pointer", fontFamily: "Sarabun", boxShadow: "0 4px 12px rgba(45,106,79,0.3)" }}>
            💰 เพิ่มรายได้
          </button>
          <button onClick={openAddExpense}
            style={{ flex: 1, background: "linear-gradient(135deg, #c0392b, #e74c3c)", color: "#fff", border: "none", borderRadius: 16, padding: "16px 8px", fontSize: 16, fontWeight: 800, cursor: "pointer", fontFamily: "Sarabun", boxShadow: "0 4px 12px rgba(192,57,43,0.3)" }}>
            💸 เพิ่มรายจ่าย
          </button>
          <button onClick={() => setView(view === "history" ? "dashboard" : "history")}
            style={{ background: "#f0f4f0", color: "#2d6a4f", border: "2px solid #2d6a4f", borderRadius: 16, padding: "16px 12px", fontSize: 22, cursor: "pointer" }}>
            📋
          </button>
        </div>
      )}
    </div>
  );
}

function SideCard({ emoji, label, accent, light, border, income, expense, net, debt }) {
  return (
    <div style={{ background: light, borderRadius: 16, padding: "14px 12px", border: `2px solid ${border}`, boxShadow: "0 2px 6px rgba(0,0,0,0.05)" }}>
      <div style={{ fontSize: 13, color: accent, fontWeight: 800, marginBottom: 10 }}>{emoji} {label}</div>
      <div style={{ marginBottom: 4 }}>
        <div style={{ fontSize: 11, color: "#888" }}>รายได้</div>
        <div style={{ fontSize: 18, fontWeight: 800, color: accent }}>+{fmt(income)}</div>
      </div>
      <div style={{ marginBottom: 4 }}>
        <div style={{ fontSize: 11, color: "#888" }}>รายจ่าย</div>
        <div style={{ fontSize: 15, fontWeight: 700, color: "#c0392b" }}>-{fmt(expense)}</div>
      </div>
      <div style={{ borderTop: "1px dashed #ccc", marginTop: 8, paddingTop: 8 }}>
        <div style={{ fontSize: 11, color: "#888" }}>คงเหลือ</div>
        <div style={{ fontSize: 18, fontWeight: 800, color: net >= 0 ? accent : "#c0392b" }}>{net >= 0 ? "+" : "-"}{fmt(Math.abs(net))}</div>
      </div>
      {debt > 0 && <div style={{ marginTop: 8, background: "#ffe0e0", borderRadius: 8, padding: "5px 8px", fontSize: 12, color: "#c0392b", fontWeight: 800 }}>⚠️ หนี้ {fmt(debt)}</div>}
    </div>
  );
}

function TxRow({ tx, onEdit, onDelete }) {
  const isIncome = tx.type === "income";
  const { day, month, year } = parseDateParts(tx.date);
  return (
    <div style={{ display: "flex", alignItems: "center", padding: "10px 0", borderBottom: "1px solid #f0f0f0", gap: 10 }}>
      <div style={{ width: 40, height: 40, borderRadius: 10, background: isIncome ? "#e8f5e9" : "#fce4ec", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 18, flexShrink: 0 }}>
        {isIncome ? "💰" : tx.party === "shared" ? "🤝" : tx.party === "garden" ? "🏡" : "🔪"}
      </div>
      <div style={{ flex: 1, minWidth: 0 }}>
        <div style={{ fontSize: 15, fontWeight: 700, color: "#1b4332", overflow: "hidden", textOverflow: "ellipsis", whiteSpace: "nowrap" }}>{tx.label || tx.note || "ขายยาง"}</div>
        <div style={{ fontSize: 12, color: "#999" }}>{day}/{month}/{year}</div>
      </div>
      <div style={{ textAlign: "right", flexShrink: 0 }}>
        <div style={{ fontSize: 16, fontWeight: 800, color: isIncome ? "#2d6a4f" : "#c0392b" }}>{isIncome ? "+" : "-"}{fmt(tx.amount)}</div>
        <div style={{ fontSize: 11, color: "#aaa" }}>บาท</div>
      </div>
      <div style={{ display: "flex", flexDirection: "column", gap: 4 }}>
        <button onClick={onEdit} style={{ background: "none", border: "none", cursor: "pointer", fontSize: 16, padding: "2px" }}>✏️</button>
        <button onClick={onDelete} style={{ background: "none", border: "none", cursor: "pointer", fontSize: 16, padding: "2px" }}>🗑️</button>
      </div>
    </div>
  );
}

function FormView({ title, onBack, onSave, children }) {
  return (
    <div style={{ padding: "14px 14px" }}>
      <div style={{ display: "flex", alignItems: "center", gap: 10, marginBottom: 18 }}>
        <button onClick={onBack} style={{ background: "#2d6a4f", color: "#fff", border: "none", borderRadius: 12, padding: "10px 16px", fontSize: 16, cursor: "pointer", fontFamily: "Sarabun", fontWeight: 700 }}>← กลับ</button>
        <div style={{ fontSize: 17, fontWeight: 800, color: "#1b4332" }}>{title}</div>
      </div>
      <div style={{ display: "flex", flexDirection: "column", gap: 16 }}>{children}</div>
      <button onClick={onSave} style={{ width: "100%", marginTop: 24, marginBottom: 20, background: "linear-gradient(135deg, #2d6a4f, #52b788)", color: "#fff", border: "none", borderRadius: 16, padding: "20px", fontSize: 20, fontWeight: 800, cursor: "pointer", fontFamily: "Sarabun", boxShadow: "0 4px 16px rgba(45,106,79,0.3)" }}>
        ✅ บันทึก
      </button>
    </div>
  );
}

function FormField({ label, children }) {
  return (
    <div>
      <div style={{ fontSize: 15, fontWeight: 700, color: "#444", marginBottom: 8 }}>{label}</div>
      {children}
    </div>
  );
}
