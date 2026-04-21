export default async function handler(req, res) {
  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader('Access-Control-Allow-Methods', 'GET, OPTIONS');
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type');
  if (req.method === 'OPTIONS') return res.status(200).end();

  const API_KEY = process.env.GEMINI_API_KEY;
  if (!API_KEY) return res.status(500).json({ error: 'API key ayarlanmamış' });

  try {
    const r = await fetch(
      `https://generativelanguage.googleapis.com/v1beta/models?key=${API_KEY}&pageSize=50`
    );
    const data = await r.json();
    if (data.error) return res.status(400).json(data);

    const models = (data.models || [])
      .filter(m =>
        m.name.includes('gemini') &&
        !m.name.includes('embedding') &&
        !m.name.includes('aqa') &&
        (m.supportedGenerationMethods || []).includes('generateContent')
      )
      .map(m => ({
        id: m.name.replace('models/', ''),
        name: m.displayName || m.name.replace('models/', '')
      }));

    const priority = ['gemini-2.5-pro','gemini-2.5-flash','gemini-2.0-flash','gemini-1.5-pro','gemini-1.5-flash'];
    models.sort((a, b) => {
      const sa = priority.findIndex(p => a.id.includes(p));
      const sb = priority.findIndex(p => b.id.includes(p));
      return (sa === -1 ? 99 : sa) - (sb === -1 ? 99 : sb);
    });

    res.status(200).json({ models });
  } catch (e) {
    res.status(500).json({ error: e.message });
  }
}
