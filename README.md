# Fractais de Sierpinski: Roteiro de Construção no GeoGebra

Material teórico e metodológico de apoio para a construção de fractais clássicos de Wacław Sierpiński utilizando o software de geometria dinâmica **GeoGebra**, desenvolvido no âmbito do **Instituto Federal do Espírito Santo (Ifes)** — **Licenciatura em Matemática • Educimat**.

O roteiro explora passo a passo como transformações geométricas de **homotetia**, combinadas ao achatamento estrutural de listas aninhadas (`Nivelar`) e a processos recursivos controlados por parâmetros dinâmicos (`ControleDeslizante` e `Iteração`), permitem modelar e visualizar a autossimilaridade característica da geometria fractal em 2D e 3D.

## Links de Acesso

- **Página do Projeto (GitHub Pages):** https://alexjordane.github.io/Fractais/
- **Documento em PDF:** [Sierpinski.pdf](./Sierpinski.pdf)
- **Código-fonte LaTeX:** [Sierpinski.tex](./Sierpinski.tex)
- **Repositório no GitHub:** https://github.com/AlexJordane/Fractais

---

## Estrutura do Material

### Capítulo 1 — Triângulo de Sierpinski (2D)
Construção passo a passo a partir de um triângulo equilátero inicial $t_1$ de vértices $A=(0,0)$, $B=(2,0)$ e $C=(1,\sqrt{3})$:
- **Transformações por Homotetia:** Estudo da sintaxe e dos parâmetros de `Homotetia(<Objeto>, <Razão>, <Ponto Central>)` com fator de contração $0{,}5$ centrado em cada vértice.
- **Achatamento de Listas (`Nivelar`):** Formalização matemática da operação de *flatten* sobre listas hierárquicas aninhadas ($\operatorname{Nivelar}(\mathcal{L}_{\text{aninhada}})$) para viabilizar etapas sucessivas (`Etapa1`, `Etapa2`, `Etapa3`, `Etapa4`).
- **Generalização Recursiva (`Iteração` e `ControleDeslizante`):** Implementação do controle dinâmico $n \in \{0, 1, \dots, 6\}$ e do comando recursivo:
  ```text
  Sierpinski = Iteração(Nivelar({Homotetia(L, 0.5, A), Homotetia(L, 0.5, B), Homotetia(L, 0.5, C)}), L, {{t1}}, n)
  ```
- **Estilização e Cores Dinâmicas (HSV):** Configuração de transparência de traço e cores dinâmicas em função do nível $n$.

### Capítulo 2 — Pirâmide de Sierpinski (3D)
Extensão tridimensional (Tetraedro de Sierpinski) na Janela de Visualização 3D do GeoGebra a partir de uma pirâmide regular $p_1$ de vértices $A, B, C, D$:
- Aplicação de 4 homotetias simultâneas de razão $0{,}5$ centradas nos vértices do tetraedro, controlada por `n = ControleDeslizante(0, 4, 1)`:
  ```text
  Sierpinski = Iteração(Nivelar({Homotetia(L, 0.5, A), Homotetia(L, 0.5, B), Homotetia(L, 0.5, C), Homotetia(L, 0.5, D)}), L, {{p1}}, n)
  ```

### Capítulo 3 — Tapete de Sierpinski (2D)
Construção recursiva a partir de um quadrado inicial $q_1$ de vértices $A, B, C, D$:
- Aplicação de 8 homotetias de razão $\frac{1}{3}$ centradas nos 4 vértices e nos 4 pontos médios dos lados do quadrado (`(A+B)/2`, `(B+C)/2`, `(C+D)/2`, `(D+A)/2`), com controle deslizante $n \in \{0, 1, 2, 3\}$:
  ```text
  Sierpinski = Iteração(Nivelar({Homotetia(L, 1/3, A), Homotetia(L, 1/3, B), Homotetia(L, 1/3, C), Homotetia(L, 1/3, D), Homotetia(L, 1/3, (A+B)/2), Homotetia(L, 1/3, (B+C)/2), Homotetia(L, 1/3, (C+D)/2), Homotetia(L, 1/3, (D+A)/2)}), L, {{q1}}, n)
  ```

---

## Arquivos do Repositório

- `Sierpinski.tex`: Código-fonte em LaTeX (classe `report`).
- `Sierpinski.pdf`: Roteiro compilado em PDF pronto para leitura e uso em laboratório.
- `Triangulo.png`, `Piramide.png`, `Tapete.png`, `GeoGebra.jpg`: Ilustrações das construções no GeoGebra utilizadas no documento.

## Como Compilar o Código LaTeX

Para gerar o PDF a partir do arquivo `Sierpinski.tex`, execute:

```bash
pdflatex Sierpinski.tex
pdflatex Sierpinski.tex
```

---

## Autoria e Licença

- **Autor:** Professor Alex Jordane (Instituto Federal do Espírito Santo — Licenciatura em Matemática • Educimat), em colaboração com Inteligência Artificial (Gemini).
- **Licença:** Esta obra está licenciada sob uma Licença **Creative Commons Atribuição-NãoComercial-SemDerivações 4.0 Internacional (CC BY-NC-ND 4.0)**. O compartilhamento e a reprodução deste material são permitidos para fins didáticos, desde que citadas a fonte e a autoria.
