- 👋 Hi, I’m @yanislav14
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
yanislav14/yanislav14 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
from reportlab.lib.pagesizes import A4
from reportlab.lib import colors
from reportlab.lib.units import cm
from reportlab.pdfgen import canvas

# Define PDF file path
pdf_file_path = "/mnt/data/Ezviz_EB3_Specifications_RO_reportlab.pdf"

# Create canvas for PDF
c = canvas.Canvas(pdf_file_path, pagesize=A4)

# Title
title = "Specificații Cameră Ezviz EB3 3MP Wi-Fi"
c.setFont("Helvetica-Bold", 16)
c.drawString(2 * cm, 28 * cm, title)

# Define sections and content
sections = {
    "Cameră și Lumină pentru Noapte": [
        "Senzor de imagine: 3 MP CMOS progresiv",
        "Rezoluție maximă: 2304 × 1296",
        "Lentilă: 2.8 mm (unghi diagonal de 131°, orizontal 110°, vertical 58°)",
        "Viziune nocturnă: până la 15 metri, atât în mod alb-negru, cât și în mod color",
        "Filtru IR automat pentru zi și noapte"
    ],
    "Video și Audio": [
        "Compresie video: H.265/H.264 pentru reducerea spațiului de stocare cu până la 50%",
        "Audio bidirecțional pentru comunicare ușoară, cu opțiunea de alerte vocale personalizabile"
    ],
    "Rețea și Conectivitate": [
        "Wi-Fi: Standard IEEE802.11b/g/n la 2.4 GHz",
        "Protocoale de securitate: WPA/WPA2, WPA-PSK/WPA2-PSK",
        "Necesită o conexiune de internet de minim 4 Mbps pentru funcționare optimă"
    ],
    "Alte Funcționalități": [
        "Alertă inteligentă cu detecție de mișcare umană și zonă de alertă personalizabilă",
        "Sirena și două lumini puternice pentru descurajarea intrușilor",
        "Design rezistent la intemperii, operabil în interval de temperatură de -20 °C până la 50 °C"
    ],
    "Stocare": [
        "Suportă card microSD până la 256 GB (achiziționat separat) și stocare în cloud (cu abonament opțional)"
    ],
    "Baterie": [
        "Capacitate de 5200 mAh, oferind o autonomie de până la 120 de zile",
        "Compatibilă și cu panouri solare pentru alimentare continuă"
    ]
}

# Positioning for content
y_position = 26 * cm
x_position = 2 * cm

# Set font for section titles and details
c.setFont("Helvetica-Bold", 14)
for section, details in sections.items():
    c.drawString(x_position, y_position, section)
    y_position -= 1 * cm  # Space after section title

    # Add each detail line in the section
    c.setFont("Helvetica", 12)
    for detail in details:
        c.drawString(x_position + 0.5 * cm, y_position, f"• {detail}")
        y_position -= 0.6 * cm

    y_position -= 0.4 * cm  # Extra space after section

# Save PDF
c.save()

pdf_file_path

