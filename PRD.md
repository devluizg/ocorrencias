# PRD - Sistema de Ocorrências Escolares

## 1. Visão do Produto

**Nome do Projeto:** Ocorrencias escolar

**Tipo:** Progressive Web App (PWA) mobile-first

**Proposta de valor:** Sistema rápido e eficiente para registro de ocorrências escolares, acessível sem login, com visualização filtrada por turmas para coordenação e relatórios individuais por aluno.

**Usuários-alvo:**
- Professores (cadastro de ocorrências)
- Coordenação (visualização e relatórios)
- Diretor (acesso completo ao sistema)

---

## 2. Personas

### Professor
- **Objetivo:** Registrar ocorrências de forma rápida durante a aula
- **Dor:** Sistemas lentos ou complicados que tiram tempo da aula
- **Necessidade:** Few taps, seleção rápida, interface mobile otimizada

### Coordenação
- **Objetivo:** Acompanhar ocorrências e identificar alunos com histórico problemático
- **Dor:** Dificuldade de filtrar e visualizar dados de forma clara
- **Necessidade:** Dashboard com filtros, relatório individual por aluno

---

## 3. Escopo Funcional

### 3.1 Módulo de Cadastro de Ocorrência (Professor)

**Campos do formulário:**
| Campo | Tipo | Obrigatório | Descrição |
|-------|------|--------------|------------|
| Nome do Aluno | Texto | Sim | Nome completo ou parcial do aluno |
| Série/Turma | Seleção | Sim | Dropdown com turmas da escola |
| Tipo de Ocorrência | Seleção | Sim | Pré-definido (ver lista abaixo) |
| Nível de Gravidade | Seleção | Sim | Leve / Médio / Grave |
| Descrição | Texto (opcional) | Não | Campo aberto para detalhes adicionais |
| Professor Responsável | Texto | Sim | Nome do professor que registrou |
| Data/Hora | Auto | Sim | Preenchido automaticamente |

**Tipos de Ocorrência (Pré-definidos):**
1. Atraso
2. Falta
3. Falta de material
4. Não realizou tarefa
5. Conversa excessiva
6. Brigas/Conflito
7. Bullying/Assédio
8. Uso de celular
9. Descumprimento de regras
10. Agressão verbal
11. Agressão física
12. Vandalismo
13. Drog/Alcool
14. Outro

**Fluxo de cadastro:**
1. Professor acessa a página inicial
2. Preenche os campos em sequência rápida
3. Botão "Salvar Ocorrência" 
4. Feedback visual de sucesso
5. Formulário limpa para próximo registro

### 3.2 Módulo de Visualização (Coordenação/Direção)

**Aba "Todas as Ocorrências":**
- Tabela responsiva com todas as ocorrências
- Colunas: Data, Aluno, Série, Tipo, Gravidade, Professor
- Ordenação por data (mais recente primeiro)

**Filtros disponíveis:**
- [ ] Por série/turma (dropdown)
- [ ] Por nível de gravidade (Leve/Médio/Grave)
- [ ] Por tipo de ocorrência
- [ ] Por nome do aluno (busca textual)
- [ ] Por período (data inicial - data final)

**Ações por linha:**
- Clicar na linha para expandir detalhes (descrição completa)
- Indicador visual de cor por gravidade:

### 3.3 Módulo de Relatórios

**Relatório Individual do Aluno:**
- Acessível ao clicar no nome do aluno na tabela
- Exibe:
  - Nome completo do aluno
  - Série/Turma
  - Total de ocorrências por gravidade
  - Timeline cronológica de todas as ocorrências
  - Gráfico simples de distribuição por tipo

**Dashboard Geral (opcional):**
- Total de ocorrências no período
- Gráfico de ocorrências por tipo
- Alunos com mais ocorrências (top 10)
- Ocorrências por dia/semana

---

## 4. Requisitos Não-Funcionais

### Performance
- Tempo de carregamento < 2 segundos em 3G
- Cadastro de ocorrência em menos de 30 segundos
- Sem necessidade de conexão constante (trabalha offline parcialmente)

### Mobile-First
- Interface otimizada para tela de celular (320px - 480px)
- Botões grandes e acessíveis (mínimo 44px de toque)
- Inputs com autocomplete para alunos e turmas
- Funciona offline após primeiro acesso (PWA)

### Armazenamento
- LocalStorage do navegador para dados locais
- Estrutura preparada para futuras sincronizações com banco de dados externo

### Segurança
- Dados permanecem no dispositivo do usuário
- Sem dados pessoais sensíveis armazenados em servidor

---

## 5. Estrutura de Navegação

```
├── Página Inicial
│   ├── [Tab 1] Nova Ocorrência (formulário)
│   ├── [Tab 2] Ocorrências (tabela com filtros)
│   └── [Tab 3] Relatórios (dashboard)
```

**Navegação inferior fixa (mobile):**
- 3 ícones/texto para alternar entre abas
- Indicador visual da aba ativa

---

## 6. Stack Tecnológica Sugerida

- **Frontend:** HTML5, CSS3, JavaScript (Vanilla ou React/Vue simples)
- **Framework PWA:** Vite + PWA Plugin ou Next.js
- **Armazenamento:** LocalStorage / IndexedDB
- **Hospedagem:** Vercel, Netlify ou GitHub Pages (gratuito)

---

## 7. Critérios de Sucesso (Definition of Done)

- [ ] Professor consegue cadastrar ocorrência em menos de 30 segundos
- [ ] Coordenação consegue filtrar ocorrências por turma
- [ ] Relatório individual mostra histórico completo do aluno
- [ ] Interface funciona perfeitamente em celular (testar em dispositivo real)
- [ ] PWA instalável na tela inicial do celular
- [ ] Visualização clara de gravidade (cores: verde/amarelo/vermelho)
- [ ] Sem necessidade de internet para cadastro (offline-capable)

---

## 8. Cronograma Sugerido (Sprints)

| Sprint | Funcionalidade |
|--------|----------------|
| Sprint 1 | Estrutura básica, formulário de ocorrência, salvamento local |
| Sprint 2 | Lista de ocorrências com filtros básicos |
| Sprint 3 | Relatório individual do aluno |
| Sprint 4 | PWA + instalação + melhorias mobile |
| Sprint 5 | Testes finais e deploy |

---

## 9. Observações Importantes

1. **Acesso público:** O sistema não exige login - qualquer pessoa com o link pode acessar
2. **Prioridade ao mobile:** Todo o design deve ser pensado para uso em celular
3. **Simplicidade:** Professor não precisa escrever descrição - apenas selecionar opções pré-definidas
4. **Escalabilidade:** Estrutura permite adicionar banco de dados no futuro

---

**Versão do PRD:** 1.0  
**Data de criação:** 09/04/2026  
**Próximos passos:** Revisão com stakeholder, criação do wireframe, início do desenvolvimento