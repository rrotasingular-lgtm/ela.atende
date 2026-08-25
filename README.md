[README (1).md](https://github.com/user-attachments/files/31430320/README.1.md)
# ela.atende

Plataforma de gestão de atendimentos — produto **Rota Soluções**.

Um app single-file (HTML + JS puro, sem build), pensado para profissionais e
pequenas equipes que precisam organizar clientes, agenda, financeiro e
documentos de atendimento em um só lugar.

## Funcionalidades

- **Meu painel** — visão geral dos atendimentos
- **Clientes** — prontuário digital de cada cliente
- **Timeline** — histórico de atendimentos por cliente
- **Agenda** — calendário de atendimentos
- **Financeiro** — receitas, despesas e pendências
- **Documentos** — arquivos, avaliações e relatórios anexados
- **Relatórios** — resumos e exportação em PDF
- **Configurações** — personalização, terminologia, conta e backup

## Como funciona

O app funciona **100% offline** por padrão, salvando tudo em `localStorage`
no aparelho. Quando conectado a um projeto Supabase, passa a sincronizar
entre dispositivos automaticamente (fila local de alterações pendentes,
processada sempre que há internet, com merge por data de atualização mais
recente).

O login usa um PIN de 4 dígitos por usuário.

## Configuração do Supabase (opcional)

Para habilitar a sincronização entre dispositivos:

1. Crie um projeto no [Supabase](https://supabase.com).
2. Configure as tabelas e as políticas de **RLS (Row Level Security)** —
   é a RLS que protege os dados, não o sigilo da chave.
3. Em *Project Settings → API*, copie a **Project URL** e a
   **anon/publishable key**.
4. Preencha as duas constantes no início do arquivo (`SUPABASE_URL` e
   `SUPABASE_PUBLISHABLE_KEY`).

> ⚠️ Nunca coloque a **service_role key** no código do app — ela é secreta
> e deve ficar apenas no backend/painel do Supabase.

Sem essas credenciais preenchidas, o app funciona normalmente, apenas sem
sincronizar entre dispositivos.

## Tecnologia

- HTML, CSS e JavaScript vanilla, em um único arquivo
- [Supabase](https://supabase.com) para autenticação e sincronização (opcional)
- Sem dependências de build — basta abrir o arquivo `.html` no navegador
