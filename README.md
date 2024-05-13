import tkinter as tk
from tkinter import messagebox, ttk

def calculate_bmi():
    try:
        height = float(height_entry.get())
        weight = float(weight_entry.get())
    except ValueError:
        messagebox.showerror("Error", "Please enter valid numbers for height and weight.")
        return

    bmi = weight / (height ** 2)

    if bmi < 17:
        result_label.config(text=f"BMI: {bmi:.2f}\nCategory: Sangat Kurus")
        advice_label.config(text="Lebih teratur lagi dalam mengkonsumsi makanan.")
    elif 17 <= bmi <= 18.5:
        result_label.config(text=f"BMI: {bmi:.2f}\nCategory: Kurus")
        advice_label.config(text="Lebih teratur lagi dalam mengkonsumsi makanan.")
    elif 18.5 <= bmi <= 25:
        result_label.config(text=f"BMI: {bmi:.2f}\nCategory: Normal")
        advice_label.config(text="Dijaga dengan teratur pola hidup seperti ini.")
    elif 25 <= bmi <= 27:
        result_label.config(text=f"BMI: {bmi:.2f}\nCategory: Gemuk (Overweight)")
        advice_label.config(text="Lebih teratur lagi dalam berolahraga dan perhatikan konsumsi makanan tinggi lemak.")
    else:
        result_label.config(text=f"BMI: {bmi:.2f}\nCategory: Gemuk (Obesitas)")
        advice_label.config(text="Lebih teratur lagi dalam berolahraga dan perhatikan konsumsi makanan tinggi lemak.")

def login():
    username = username_entry.get()
    password = password_entry.get()

    # Verifikasi username dan password di sini
    if username == "kalkulator BMI" and password == "pastisehat":
        login_frame.pack_forget()  # Hide login frame
        bmi_frame.pack()  # Show BMI frame
    else:
        messagebox.showerror("Login", "Login gagal!")

root = tk.Tk()
root.title("Kalkulator BMI")

# Login Frame
login_frame = tk.Frame(root, padx=20, pady=20)
login_frame.pack()

title_label = tk.Label(login_frame, text="Form Login", font=("Arial", 16))
title_label.grid(row=0, column=0, columnspan=2, pady=10)

username_label = tk.Label(login_frame, text="Username:")
username_label.grid(row=1, column=0, pady=5)
username_entry = tk.Entry(login_frame)
username_entry.grid(row=1, column=1, pady=5)

password_label = tk.Label(login_frame, text="Password:")
password_label.grid(row=2, column=0, pady=5)
password_entry = tk.Entry(login_frame, show="*")
password_entry.grid(row=2, column=1, pady=5)

login_button = tk.Button(login_frame, text="Login", command=login)
login_button.grid(row=3, column=0, columnspan=2, pady=10)

# BMI Frame
bmi_frame = tk.Frame(root, padx=20, pady=20)

height_label = tk.Label(bmi_frame, text="Tinggi Badan (meter):")
height_label.grid(row=0, column=0, padx=5, pady=5)
height_entry = tk.Entry(bmi_frame)
height_entry.grid(row=0, column=1, padx=5, pady=5)

weight_label = tk.Label(bmi_frame, text="Berat Badan (kg):")
weight_label.grid(row=1, column=0, padx=5, pady=5)
weight_entry = tk.Entry(bmi_frame)
weight_entry.grid(row=1, column=1, padx=5, pady=5)

calculate_button = tk.Button(bmi_frame, text="Hitung BMI", command=calculate_bmi)
calculate_button.grid(row=2, column=0, columnspan=2, padx=5, pady=5)

result_label = tk.Label(bmi_frame, text="", font=("Arial", 12))
result_label.grid(row=3, column=0, columnspan=2, padx=5, pady=5)

advice_label = tk.Label(bmi_frame, text="", font=("Arial", 12))
advice_label.grid(row=4, column=0, columnspan=2, padx=5, pady=5)

root.mainloop()
