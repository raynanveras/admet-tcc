# Como colocar este site no ar (GitHub Pages)

O resultado é um endereço público e permanente, do tipo
`https://SEU-USUARIO.github.io/admet-tcc/`, que a banca abre em qualquer navegador,
sem instalar nada e sem precisar de conta.

Escolha **uma** das duas vias abaixo. A primeira não exige git.

---

## Via A — pelo site do GitHub (sem linha de comando)

**1. Crie a conta**, se ainda não tiver: <https://github.com/signup>

**2. Crie o repositório**
   - <https://github.com/new>
   - Nome: `admet-tcc`
   - Marque **Public** (o GitHub Pages gratuito exige repositório público)
   - **Não** marque "Add a README file" — já existe um aqui
   - Clique em *Create repository*

**3. Envie os arquivos**
   - Na página do repositório vazio, clique em **uploading an existing file**
   - Abra esta pasta (`admet/site/`) no gerenciador de arquivos
   - Selecione **tudo**, inclusive as pastas `figuras/` e `dados/`, e arraste para a
     área de upload do navegador
   - O arquivo `.nojekyll` é oculto: no Linux, aperte **Ctrl+H** no gerenciador de
     arquivos para mostrá-lo antes de arrastar. Ele é pequeno mas necessário.
   - Escreva algo em *Commit changes* e confirme

**4. Ligue o Pages**
   - Aba **Settings** → menu lateral **Pages**
   - Em *Source*, escolha **Deploy from a branch**
   - Branch: **main**, pasta: **/ (root)** → *Save*

**5. Espere de 1 a 3 minutos.** Recarregue a página de Settings → Pages: o endereço
   aparece no topo, em uma faixa verde.

---

## Via B — pela linha de comando

Requer git instalado (`git --version` para conferir).

```bash
cd /media/mariliacecilias/3718785121005F7F/Raynan/TCC/Docking_9XYG/admet/site

git init -b main
git add -A
git commit -m "Material suplementar ADMET do TCC: painel, figuras e dados"

# troque SEU-USUARIO pelo seu nome de usuário no GitHub
git remote add origin https://github.com/SEU-USUARIO/admet-tcc.git
git push -u origin main
```

O repositório `admet-tcc` precisa existir antes (passo 2 da via A), e o push vai pedir
autenticação: use um **personal access token** como senha, não a senha da conta
(<https://github.com/settings/tokens> → *Generate new token (classic)* → marque o
escopo `repo`). Depois siga o passo 4 da via A para ligar o Pages.

Se tiver o `gh` instalado, os três últimos comandos viram um só:

```bash
gh repo create admet-tcc --public --source=. --push
```

---

## Depois que estiver no ar

**Corrija os links do README.** Abra `README.md` e troque as duas ocorrências de
`SEU-USUARIO` pelo seu usuário real. Sem isso os links no topo apontam para lugar
nenhum. (Pelo site: abra o arquivo no GitHub e clique no lápis.)

**Confira em uma aba anônima**, para garantir que a banca vê o mesmo que você.

**Para citar no TCC**, algo nessa linha:

> Material suplementar — painel interativo com as 73 predições ADMET por ligante.
> Disponível em: https://SEU-USUARIO.github.io/admet-tcc/. Acesso em: DD mmm. AAAA.

Se quiser um endereço que não mude caso você renomeie o repositório, vale registrar
um DOI no Zenodo e citá-lo em vez da URL — o Zenodo se conecta ao GitHub e arquiva
uma versão a cada release.

---

## Atualizar depois

Trocou alguma figura ou refez a análise? Regere os arquivos e substitua-os no
repositório (via A: *Add file → Upload files*, que sobrescreve os de mesmo nome;
via B: `git add -A && git commit -m "..." && git push`). O site atualiza sozinho em
um ou dois minutos.

## Observações

- Tudo aqui é estático: nenhum servidor, nenhuma dependência, nada que expire.
  O painel funciona offline também, se alguém baixar o `index.html`.
- O repositório precisa ser público. Se preferir não deixar os dados abertos, a
  alternativa é mandar o `index.html` por e-mail — ele funciona sozinho, com os
  dados embutidos.
