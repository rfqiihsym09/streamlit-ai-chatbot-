# streamlit-ai-chatbot-
berikut ChatBot AI yang saya bikin dengan dibantu dengan ChatGPT, to be honest im first time in learn Coding etc. cmiiw and raise up if i have false. thank so much!
import { useState } from "react";
import { MessageCircle, Send } from "lucide-react";

export default function ChatbotPreview() {
  const [msgs, setMsgs] = useState([
    { role: "assistant", content: "Halo! Aku chatbot AI. Ada yang bisa kubantu?" },
    { role: "user", content: "Tolong buatkan ringkasan artikel ini." },
    { role: "assistant", content: "Tentu! Unggah teksnya, nanti akan kuringkas secara ringkas dan jelas." },
  ]);
  const [input, setInput] = useState("");

  return (
    <div className="min-h-screen w-full bg-gray-50 flex items-center justify-center p-6">
      <div className="w-full max-w-3xl">
        <div className="bg-white rounded-2xl shadow-xl border overflow-hidden">
          <div className="px-6 py-4 border-b bg-indigo-600 text-white flex items-center gap-2">
            <MessageCircle className="w-5 h-5" />
            <h1 className="text-lg font-semibold">AI Chat Bot</h1>
            <span className="ml-auto text-xs opacity-90">Streamlit UI (mock preview)</span>
          </div>

          <div className="h-[520px] overflow-y-auto p-6 space-y-4 bg-gradient-to-b from-white to-indigo-50/40">
            {msgs.map((m, i) => (
              <div key={i} className={`flex ${m.role === "user" ? "justify-end" : "justify-start"}`}>
                <div
                  className={`max-w-[78%] rounded-2xl px-4 py-3 text-sm shadow ${
                    m.role === "user"
                      ? "bg-indigo-600 text-white rounded-br-sm"
                      : "bg-white border rounded-bl-sm"
                  }`}
                >
                  {m.content}
                </div>
              </div>
            ))}
          </div>

          <div className="p-4 border-t bg-white">
            <div className="flex items-center gap-2">
              <input
                value={input}
                onChange={(e) => setInput(e.target.value)}
                placeholder="Ketik pesan..."
                className="flex-1 rounded-xl border px-4 py-3 text-sm focus:outline-none focus:ring-2 focus:ring-indigo-400"
              />
              <button
                onClick={() => {
                  if (!input.trim()) return;
                  setMsgs([...msgs, { role: "user", content: input }]);
                  setInput("");
                }}
                className="rounded-xl border px-4 py-3 text-sm shadow hover:shadow-md active:scale-[.98]"
              >
                <Send className="w-4 h-4" />
              </button>
            </div>
            <div className="text-xs text-gray-500 mt-2">
              Sidebar (tidak ditampilkan di mock) akan berisi: pilihan model, temperature, system prompt, dan input API key.
            </div>
          </div>
        </div>
      </div>
    </div>
  );
}
