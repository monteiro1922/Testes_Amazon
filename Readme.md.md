# Casos de Teste — Amazon.com.br (Busca, Filtros e Ordenação)

Suite de casos de teste manuais focada na validação de busca de produtos, filtragem por faixa de preço, ordenação de resultados e exibição de informações no card de produto na plataforma **Amazon.com.br**.

## 📋 Visão Geral e Ambiente

* **Sistema testado:** [Amazon.com.br](https://www.amazon.com.br)
* **Ambiente:** Google Chrome, Windows 11 (Desktop)
* **Perfil de usuário:** Visitante não autenticado

## 🧪 Casos de Teste

| ID | Título do caso de teste | Pré-condição | Dado de teste | Resultado esperado | Resultado obtido | Status |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **CT-01** | Buscar produto existente pelo nome | Estar na página inicial do site, sem login | `"fone de ouvido bluetooth"` | A página de resultados exibe produtos relacionados a fones de ouvido bluetooth | Resultados exibidos são coerentes com o termo buscado | Passou |
| **CT-02** | Buscar termo sem resultados | Estar na página inicial do site | `"xyzabc123produtoinexistente"` | O site exibe mensagem informando que nenhum resultado foi encontrado | Mensagem de nenhum resultado exibida corretamente | Passou |
| **CT-03** | Executar busca com campo vazio | Estar na página inicial do site | `(campo em branco)` | O site permanece na página ou exibe listagem geral, sem erro para o usuário | Página exibe listagem geral sem mensagem de erro | Passou |
| **CT-04** | Aplicar filtro de faixa de preço | Ter executado a busca do CT-01 com resultados na tela | `Faixa: até R$ 100,00` | Somente produtos com preço até R$100 permanecem na lista | Na nova execução, após selecionar a faixa até R$ 100,00, a listagem apresentou somente produtos dentro do limite selecionado. | Passou |
| **CT-05** | Ordenar resultados por menor preço | Ter executado a busca do CT-01 com resultados na tela | `Ordenação: Preço: menor para maior` | Os produtos são exibidos em ordem crescente de preço | Ordem crescente de preço aplicada corretamente | Passou |
| **CT-06** | Validar informações exibidas no card do produto | Ter uma lista de resultados na tela | `Primeiro resultado da busca do CT-01` | O card exibe, no mínimo, nome e preço do produto de forma legível | Nome, preço e avaliação exibidos corretamente | Passou |

### Passos de Execução por Caso de Teste

* **CT-01:** 1. Acessar amazon.com.br → 2. Clicar na barra de busca → 3. Digitar o termo → 4. Pressionar Enter.
* **CT-02:** 1. Acessar amazon.com.br → 2. Digitar um termo sem correspondência → 3. Pressionar Enter.
* **CT-03:** 1. Acessar amazon.com.br → 2. Deixar a barra de busca vazia → 3. Pressionar Enter.
* **CT-04:** 1. Na coluna de filtros, localizar a faixa de preço → 2. Selecionar a faixa até R$100 → 3. Aguardar a lista recarregar.
* **CT-05:** 1. Abrir o seletor de ordenação → 2. Escolher a opção de menor preço → 3. Observar a ordem da lista.
* **CT-06:** 1. Observar o primeiro card de resultado → 2. Verificar nome, preço e avaliação.

## 📊 Resumo da Execução

| Métrica | Valor |
| :--- | :--- |
| **Total de casos executados** | 6 |
| **Casos aprovados (Passou)** | 6 |
| **Casos reprovados (Falhou)** | 0 |
| **Taxa de aprovação** | 100,0% |

## 🔁 Histórico de Reteste

* **CT-04:** Primeira execução: *Falhou* — foram observados produtos acima de R$ 100,00. Após nova execução selecionando a faixa até R$ 100,00, passou a exibir apenas itens dentro do limite.

## 🚀 Próximos Passos

* **Expansão de cenários:** Adicionar casos de teste para combinação simultânea de múltiplos filtros (marca, avaliação de clientes e frete grátis) e paginação de resultados.
* **Automação E2E:** Implementar os fluxos críticos (busca, filtragem e ordenação) utilizando **Cypress** para execução automatizada de regressão.
* **Evidências de execução:** Anexar capturas de tela dos resultados obtidos e do reteste do **CT-04** em uma pasta `/evidencias` no repositório.
* **Testes de responsividade:** Validar o comportamento da barra de busca e dos filtros em viewports mobile.