# CAIXA — Análise estática e entrega

## Descrição
Repositório contendo análise estática (caixa branca) do código fornecido, planilha de teste, código comentado e testes unitários (mocked).

## Arquivos incluídos
- Planilha_Teste_caixa.xlsx — planilha de teste estático (formato banner).  
- User_Caixa.java — código corrigido e comentado.  
- TestUserCaixa.java — testes unitários com Mockito (mock de conexão).  
- Entrega_EasyMusic_Sumario.pdf — sumário (já gerado).

## Notação de Grafo de Fluxo (método verificarUsuario)
Nós e Arestas (simplificado):
1. Start
2. conectarBD()
3. montar SQL e preparar PreparedStatement
4. executeQuery()
5. rs.next() ? (decisão)
   - se true -> obter nome, set usuarioValido = true
   - se false -> usuarioValido = false
6. return usuarioValido
7. End

Representação visual (ASCII):

Start -> conectarBD -> prepararStatement -> executeQuery -> [rs.next?] --Yes--> atribuir nome -> return true -> End
                                                   \--No--> return false -> End

## Cálculo da Complexidade Ciclomática
Usamos fórmula: M = D + 1, onde D = número de decisões (condicionais/branches) no método.

No método `verificarUsuario` há apenas **1 decisão** (if rs.next()).
Portanto:
M = 1 + 1 = **2**

**Interpretação:** Complexidade baixa; existem 2 caminhos básicos de execução.

## Caminhos Básicos (enumerados)
1. **Usuário encontrado**: conectarBD -> prepararStatement -> executeQuery -> rs.next() == true -> ler nome -> retorna true
2. **Usuário não encontrado**: conectarBD -> prepararStatement -> executeQuery -> rs.next() == false -> retorna false

## Testes
Incluí `TestUserCaixa.java` que usa Mockito para simular o comportamento do BD e validar os dois caminhos acima.
Para executar localmente com Maven, adicione dependências junit-jupiter e mockito-core e rode `mvn test`.

## Como criar o repositório remoto (passos)
**Opção A — usando GitHub CLI (`gh`)** (recomendado se tiver `gh` instalado):

```bash
git init
git add .
git commit -m "Entrega CAIXA - análise estática, planilha e código"
gh repo create seu-usuario/caixa --public --source=. --remote=origin --push
```

**Opção B — sem `gh` (via GitHub web)**:
1. No GitHub, clique em "New repository". Nomeie como `caixa` e deixe público.
2. Siga as instruções para conectar seu repositório local (git remote add origin ... && git push -u origin master).

## Observações finais
- Não tenho acesso direto para criar o repositório remoto no seu GitHub por questões de segurança.  
- Posso gerar um arquivo ZIP com todos os arquivos para você subir manualmente — forneço o link para download abaixo.
