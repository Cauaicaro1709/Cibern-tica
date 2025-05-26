
# Proteção contra SQL Injection e Ataques de Força Bruta em Aplicações Web

Este repositório apresenta exemplos práticos em PHP, ilustrando tanto vulnerabilidades quanto boas práticas para prevenir **SQL Injection** e ataques por **força bruta**.

## 📁 Conteúdo

- `inseguro.php`: Implementação propositalmente vulnerável, sem proteção contra injeção de SQL ou múltiplas tentativas de login.
- `seguro.php`: Versão com medidas de segurança aplicadas:
  - Utilização de `PDO` com *prepared statements* para impedir SQL Injection.
  - Monitoramento de tentativas de login com `$_SESSION`, dificultando ataques automatizados.
  - Verificação de senhas com `password_verify()` ao invés de comparações diretas.

## 🔐 Mecanismos de Defesa Implementados

| Ataque identificado   | Estratégia de mitigação                          |
|------------------------|--------------------------------------------------|
| Injeção de SQL         | Utilização de `prepare()` e `bindParam()` do PDO |
| Força bruta            | Controle de tentativas por sessão PHP           |
| Senhas expostas        | Aplicação de `password_hash()` e `password_verify()` |

## 📝 Dicas de Segurança

Para garantir que as senhas sejam armazenadas de forma segura no banco de dados, utilize:

```php
$senha_hash = password_hash($senha, PASSWORD_DEFAULT);
