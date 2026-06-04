# Linux Fundamentals Part 1 — TryHackMe

## Navegação de Diretórios

### pwd — Print Working Directory
Mostra o caminho completo do diretório atual.
```bash
pwd
```

### ls — List
Lista arquivos e diretórios do diretório atual.
```bash
ls
ls -a  # mostra arquivos ocultos
```

### cd — Change Directory
Navega entre diretórios.
```bash
cd pasta
cd ..        # volta um nível
cd /         # vai para a raiz
```

## Leitura de Arquivos

### cat — Concatenate
Exibe o conteúdo de um arquivo.
```bash
cat arquivo.txt
```

## Busca de Arquivos

### find
Busca arquivos no sistema.
```bash
find -name arquivo.txt        # busca por nome
find -name *.txt              # busca todos os .txt
find / -name arquivo.txt      # busca a partir da raiz
```

### grep
Busca um termo dentro do conteúdo de um arquivo.
```bash
grep "termo" arquivo.txt
grep "THM" access.log
```

## Operadores de Shell

| Operador | Função |
|---|---|
| `&` | Roda comando em segundo plano |
| `&&` | Roda segundo comando só se o primeiro funcionar |
| `>` | Redireciona output para um arquivo (sobrescreve) |
| `>>` | Redireciona output para um arquivo (adiciona ao final) |
