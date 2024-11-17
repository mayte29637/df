- 👋 Hi, I’m @mayte29637
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
import tkinter as tk
from tkinter import messagebox

# Configuración inicial
class SaludGame:
    def __init__(self, root):
        self.root = root
        self.root.title("Gestor de Salud Pública")
        
        # Variables del juego
        self.poblacion = 1000000
        self.recursos = 1000
        self.satisfaccion = 50
        self.salud_publica = 50
        
        # Interfaz
        self.create_widgets()

    def create_widgets(self):
        # Etiquetas de estado
        self.label_poblacion = tk.Label(self.root, text=f"Población: {self.poblacion}")
        self.label_poblacion.pack()

        self.label_recursos = tk.Label(self.root, text=f"Recursos: {self.recursos}")
        self.label_recursos.pack()

        self.label_satisfaccion = tk.Label(self.root, text=f"Satisfacción: {self.satisfaccion}")
        self.label_satisfaccion.pack()

        self.label_salud = tk.Label(self.root, text=f"Salud Pública: {self.salud_publica}")
        self.label_salud.pack()

        # Botones de acciones
        tk.Button(self.root, text="Promover vacunación", command=self.promover_vacunacion).pack(pady=5)
        tk.Button(self.root, text="Construir centros de salud", command=self.construir_centros).pack(pady=5)
        tk.Button(self.root, text="Campañas educativas", command=self.campana_educativa).pack(pady=5)
        tk.Button(self.root, text="Inversión en tecnología médica", command=self.invertir_tecnologia).pack(pady=5)
        tk.Button(self.root, text="Simular crisis sanitaria", command=self.crisis_sanitaria).pack(pady=5)

    # Acciones del jugador
    def promover_vacunacion(self):
        if self.recursos >= 100:
            self.recursos -= 100
            self.salud_publica += 10
            self.satisfaccion += 5
            self.update_labels("Promoción de vacunación exitosa.")
        else:
            self.update_labels("Recursos insuficientes para la vacunación.")

    def construir_centros(self):
        if self.recursos >= 300:
            self.recursos -= 300
            self.salud_publica += 15
            self.satisfaccion += 10
            self.update_labels("Se construyeron nuevos centros de salud.")
        else:
            self.update_labels("Recursos insuficientes para construir centros de salud.")

    def campana_educativa(self):
        if self.recursos >= 50:
            self.recursos -= 50
            self.satisfaccion += 10
            self.salud_publica += 5
            self.update_labels("Campaña educativa exitosa.")
        else:
            self.update_labels("Recursos insuficientes para una campaña educativa.")

    def invertir_tecnologia(self):
        if self.recursos >= 200:
            self.recursos -= 200
            self.salud_publica += 20
            self.update_labels("Se mejoró la tecnología médica.")
        else:
            self.update_labels("Recursos insuficientes para inversión en tecnología.")

    def crisis_sanitaria(self):
        impacto = 20
        self.salud_publica -= impacto
        self.satisfaccion -= impacto // 2
        self.update_labels("¡Crisis sanitaria! La salud pública y la satisfacción han disminuido.")

    # Actualizar etiquetas y verificar estado
    def update_labels(self, mensaje):
        self.label_poblacion.config(text=f"Población: {self.poblacion}")
        self.label_recursos.config(text=f"Recursos: {self.recursos}")
        self.label_satisfaccion.config(text=f"Satisfacción: {self.satisfaccion}")
        self.label_salud.config(text=f"Salud Pública: {self.salud_publica}")
        messagebox.showinfo("Información", mensaje)

        # Verificar si el jugador pierde
        if self.salud_publica <= 0:
            messagebox.showerror("Fin del juego", "La salud pública ha colapsado. Inténtalo de nuevo.")
            self.root.destroy()

# Inicializar el juego
if __name__ == "__main__":
    root = tk.Tk()
    app = SaludGame(root)
    root.mainloop()

<!---
mayte29637/mayte29637 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
