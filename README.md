import json
import zipfile
from pathlib import Path

# Crear JSON de ejemplo
data = {
    "preguntas": [
        {
            "tema": "malware",
            "respuesta": "🦠 Malware is malicious software that harms your device or data. Use antivirus software and avoid suspicious downloads."
        },
        {
            "tema": "phishing",
            "respuesta": "🎣 Phishing is a scam where attackers try to trick you into giving personal info. Don't click unknown links in emails."
        },
        {
            "tema": "2FA",
            "respuesta": "🔐 Two-Factor Authentication adds an extra layer of protection to your accounts. Always enable it when possible."
        },
        {
            "tema": "password",
            "respuesta": "🔑 Use strong passwords (at least 12 characters, with symbols, numbers and uppercase letters). Avoid reusing them!"
        }
    ]
}

# Guardar JSON como archivo
json_path = Path("/mnt/data/chatbot_cybersecurity.json")
with open(json_path, "w") as json_file:
    json.dump(data, json_file, indent=2)

# Crear un archivo ZIP
zip_path = Path("/mnt/data/chatbot_cybersecurity.zip")
with zipfile.ZipFile(zip_path, "w") as zipf:
    zipf.write(json_path, arcname="chatbot_cybersecurity.json")

zip_path
