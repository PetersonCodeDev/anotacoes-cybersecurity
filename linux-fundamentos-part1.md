# Linux Fundamentals Part 1 — TryHackMe

## Navegação de Diretórios

### pwd — Print Working Directory

Mostra o caminho completo do diretório atual.

```
pwd
```

### ls — List

Lista arquivos e diretórios do diretório atual.

```
ls
ls -a  # mostra arquivos ocultos
```

### cd — Change Directory

Navega entre diretórios.

```
cd pasta
cd ..        # volta um nível
cd /         # vai para a raiz
```

## Leitura de Arquivos

### cat — Concatenate

Exibe o conteúdo de um arquivo.

```
cat arquivo.txt
cat ./arquivo    # arquivos com nome especial (hífen, espaço)
cat ./-arquivo   # arquivo cujo nome começa com hífen
```

## Busca de Arquivos

### find

Busca arquivos no sistema.

```
find -name arquivo.txt        # busca por nome
find -name *.txt              # busca todos os .txt
find / -name arquivo.txt      # busca a partir da raiz
find . -size 1033c            # busca por tamanho em bytes
find / -user bandit7          # busca por dono do arquivo
find / -group bandit6         # busca por grupo do arquivo
find / -size 33c -user bandit7 -group bandit6  # combinando filtros
```

### grep

Busca um termo dentro do conteúdo de um arquivo.

```
grep "termo" arquivo.txt
grep "THM" access.log
grep millionth data.txt       # sem aspas funciona pra palavras simples
grep "frase com espaço" arquivo.txt  # aspas necessárias com espaços
```

## Operadores de Shell

| Operador | Função |
| -------- | ------ |
| `&`      | Roda comando em segundo plano |
| `&&`     | Roda segundo comando só se o primeiro funcionar |
| `>`      | Redireciona output para um arquivo (sobrescreve) |
| `>>`     | Redireciona output para um arquivo (adiciona ao final) |
| `\|`     | Pipe — passa o output de um comando como input do próximo |

## Comandos Avançados

### file

Identifica o tipo de um arquivo.

```
file arquivo        # mostra se é texto, binário, etc
file ./-file0*      # verifica vários arquivos de uma vez
```

### sort

Ordena as linhas de um arquivo alfabeticamente.

```
sort arquivo.txt
```

### uniq

Filtra linhas duplicadas. Necessita que as linhas estejam ordenadas.

```
uniq arquivo.txt       # remove duplicatas
uniq -u arquivo.txt    # mostra só linhas únicas (sem duplicata)
```

### strings

Extrai texto legível de arquivos binários.

```
strings arquivo_binario
```

### base64

Codifica e decodifica Base64.

```
base64 -d arquivo.txt    # decodifica
```

## Combinando Comandos com Pipe

O pipe `|` conecta comandos — o output do primeiro vira input do segundo.

```
sort data.txt | uniq -u               # acha linha que aparece só uma vez
strings data.txt | grep "=="          # acha strings com == em arquivo binário
cat arquivo.txt | grep "palavra"      # filtra palavra no conteúdo
```

## Dicas de Terminal

- **Tab** — autocompleta nomes de arquivo e pasta
- **Ctrl+C** — cancela comando em execução
- **Ctrl+Shift+C** — copia texto do terminal
- **Ctrl+Shift+V** — cola texto no terminal
- `./` antes do nome — acessa arquivos com nomes problemáticos (hífen, espaço)

## OverTheWire Bandit — Progresso

| Nível | Técnica aprendida |
|-------|------------------|
| 0→1   | `cat` básico, SSH |
| 1→2   | `./` para arquivos com hífen |
| 2→3   | Tab completion, espaços em nomes |
| 3→4   | `ls -a` para arquivos ocultos |
| 4→5   | `file` para identificar tipo, `./` com hífen |
| 5→6   | `find` com `-size` |
| 6→7   | `find` com `-user`, `-group`, busca em `/` |
| 7→8   | `grep` para filtrar texto |
| 8→9   | `sort` + `uniq -u` para linha única |
| 9→10  | `strings` + `grep` em arquivo binário |
| 10→11 | `base64 -d` para decodificar |
