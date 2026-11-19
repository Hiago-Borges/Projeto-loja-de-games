# 🎮 Borges Games

Loja virtual de jogos digitais — PHP 8.1+, MySQL, PDO, POO e arquitetura MVC.
Autor: Carlos Eduardo R.B — UNIFIPMoc

## Como rodar (XAMPP / Laragon / WAMP)
1. Copie a pasta para `htdocs/borges_games_psn` (Apache com `mod_rewrite` ligado).
2. No phpMyAdmin, aba **SQL**, cole e execute `database/banco.sql` (recria o banco `borges_games` com dados de teste).
3. Se necessário, ajuste usuário/senha do MySQL em `config/config.php`.
4. Abra `http://localhost/borges_games_psn/`.

Sem Apache/XAMPP: `php -S localhost:8000 -t public public/index.php`.

### Contas de teste
| Perfil | E-mail | Senha |
|---|---|---|
| Administrador | admin@borges.games | admin123 |
| Gerente | gerente@borges.games | admin123 |
| Cliente | ana@email.com | cliente123 |

## Estrutura
```
public/            único diretório web: index.php (front controller), css/, js/, uploads/
app/Core/          Router, Controller, Model, View, Database (PDO), Session, Validator, Upload, Carrinho
app/Models/        Usuario, Cliente, Categoria, Game, Pedido  (SQL com prepared statements)
app/Controllers/   Home, Jogo, Carrinho, Auth, Conta  +  Admin/ (Dashboard, Game, Categoria, Cliente, Usuario, Pedido, Relatorio)
app/Views/         layouts/ (publico, admin, auth), parciais/ e uma pasta por módulo
config/            config.php (banco) e routes.php (todas as rotas)
database/banco.sql script completo      docs/  Etapa 1 (regras, UML, MER)
```

## Requisitos do trabalho
- **PHP 8, MySQL, PDO, POO, MVC, banco relacional** ✔
- **Autenticação e sessão**: login/logout, `password_hash()`, `session_regenerate_id`, middlewares `guest/auth/cliente/admin/superadmin`, área admin protegida ✔
- **Página inicial pública** com dados do banco, busca e filtro ✔ · **Registro de cliente** (nome, e-mail, telefone, senha) ✔
- **5 CRUDs completos**: Usuário, Cliente, Categoria, Game, Pedido ✔
- **Funcionalidades extras (9)**: busca, filtro por categoria, upload de imagem, carrinho, controle de estoque, relatório de vendas, dashboard, página de detalhes, validação JS ✔
- Segurança: CSRF em todo POST, XSS (`e()`), SQL injection (prepared statements), upload validado por MIME, exclusão só via POST.

## Rotas principais
`/` · `/jogo/{id}` · `/carrinho` · `/login` · `/cadastro` · `/conta` · `/conta/pedidos` · `/admin` · `/admin/{games|categorias|clientes|usuarios|pedidos|relatorios}`
