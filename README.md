import customtkinter as ctk
from PIL import Image, ImageTk

# Aparência
ctk.set_appearance_mode('light')
ctk.set_default_color_theme('blue') 


# Função da validação de login
def validar_login():
    usuario = entry_usuario.get()
    senha = entry_senha.get()
    
    if usuario == 'Túlio' and senha == '12345678':
        resultado_login.configure(text='✅ Login feito com sucesso!', text_color='green')
    else:
        resultado_login.configure(text='❌ Login incorreto', text_color='red')
        
# Janela principal
app = ctk.CTk()
app.title('Sistema de Login')
app.geometry('700x650')
app.resizable(False, False) 

# Título da tela
titulo = ctk.CTkLabel(app, text='Faça login', font=('Arial', 25, 'bold'))
titulo.pack(pady=20)

#imagem da tela
imagem = Image.open(r"c:\Users\tulio\Downloads\login.png")
imagem = imagem.resize((150, 150))
imagem_tk = ImageTk.PhotoImage(imagem)

label_imagem = ctk.CTkLabel(app, image=imagem_tk, text="") 
label_imagem.image = imagem_tk 
label_imagem.pack(pady=5)

# Campo de usuário
label_usuario = ctk.CTkLabel(app, text='Usuário:')
label_usuario.pack()
entry_usuario = ctk.CTkEntry(app, placeholder_text='Digite seu usuário')
entry_usuario.pack(pady=5)

# Campo de senha
label_senha = ctk.CTkLabel(app, text='Senha:')
label_senha.pack()
entry_senha = ctk.CTkEntry(app, placeholder_text='Digite sua senha', show='*')
entry_senha.pack(pady=5)


# Botão de login
botao_login = ctk.CTkButton(app, text='Entrar', command=validar_login)
botao_login.pack(pady=15)

# Resultado (feedback)
resultado_login = ctk.CTkLabel(app, text='')
resultado_login.pack(pady=10)

# Executar app
app.mainloop()
