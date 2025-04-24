# SavioProjetos

  Automação em Python - Nesse projeto é recriado uma situação de cadastro de produtos automaticamente em determinado site -
  
  Ferramentas utilizadas: Pyautogui; time; pandas;
  
    import pyautogui
    import time
    #pyautogui.write -> escrever
    #pyautogui.click -> clica com o mouse
    #pyautogui.press -> apertar uma tecla
    #pyautogui.hotkey -> atalhos
  
    pyautogui.PAUSE = 0.3
    
    #abrir no navegaodor:
    pyautogui.press("win")
    pyautogui.write("chrome")
    pyautogui.press("enter")
    time.sleep(1)
    pyautogui.click(x=1345, y=59)
    time.sleep(1)
    pyautogui.click(x=956, y=592)
    time.sleep(1)
    pyautogui.click(x=673, y=68)
    # Passo 2: fazer login
    link = "https://dlp.hashtagtreinamentos.com/python/intensivao/login"
    pyautogui.write(link)
    pyautogui.press("enter")
  
    #quero dar uma pausa
    time.sleep(2)
    pyautogui.click(x=697, y=376)
    pyautogui.write("p")
    #passar para o proximo campo
    pyautogui.press("tab")
    pyautogui.write("123")
    #passando pra o botao de logar
    pyautogui.press("tab")
    pyautogui.press("enter")
  
    time.sleep(1)
    
    # Passo 3: Importar a base de dados
    import pandas
    
    tabela = pandas.read_csv('produtos.csv')
    print(tabela)
    
    # Passo 4: Cadastrar um produto
    pyautogui.click(x=722, y=254)
    
    for linha in tabela.index:
  
      pyautogui.click(x=722, y=254)
      #codigo
      codigo = tabela.loc[linha, "codigo"]
      pyautogui.write(str(codigo))
      pyautogui.press("tab")

    #marca
    marca = tabela.loc[linha, "marca"]
    pyautogui.write(str(marca))
    pyautogui.press("tab")

    #tipo
    tipo = tabela.loc[linha, "tipo"]
    pyautogui.write(str(tipo))
    pyautogui.press("tab")

    #categoria
    categoria = tabela.loc[linha, "categoria"]
    pyautogui.write(str(categoria))
    pyautogui.press("tab")

    #preco
    preco = tabela.loc[linha, "preco_unitario"]
    pyautogui.write(str(preco))
    pyautogui.press("tab")

    #custo
    custo = tabela.loc[linha, "custo"]
    pyautogui.write(str(custo))
    pyautogui.press("tab")

    #obs
    obs = tabela.loc[linha, "obs"]
    if not pandas.isna(obs):
        pyautogui.write(str(obs))
    pyautogui.press("tab")

    #clicar no botao enviar
    pyautogui.press("enter")
    pyautogui.scroll(5000)
# Passo 5: Repetir até acabar

