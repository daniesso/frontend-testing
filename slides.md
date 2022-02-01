# Frontend testing

Bekk workshop - Februar 2022

---

### Oss

| ![](img/daniel.jpg) | ![](img/erlend.jpg) | ![](img/aina.jpg) |
| :-----------------: | :-----------------: | :---------------: |
|       Daniel        |       Erlend        |       Aina        |

---

### Bekk

- Konsulenter innen teknologi, design og forretningsrådgiving
- Kontorer i Oslo og Trondheim
- 517 ansatte (52 i Trondheim)
- Snittalder 32

---

### Bekk

- Fokus på faglig utvikling
- Faggrupper 2022 i Trondheim:
  - Spillutvikling
  - Lederskap og Kommunikasjon
  - Appgarasjen
  - Smart-kontor
  - Nøtteknekkerne
- Fagdager og faggruppedager

---

### Spirit

- Ansvarlig for det sosiale i Bekk
- Aktivitetstilbud
- Festligheter
- Spirit Fond

---

### Plan for i kveld

- 16:30 Intro
- 17:00 Oppgaver i Cypress og Jest
- 19:20 Vi drar til Cafe Løkka

---

### Frontend testing 💡

---

### Hva er en god test?

- Rask
- Forutsigbar og repeterbar
- Isolert
- Tester grensesnitt, ikke implementasjon

---

### Hvilken type tester har man?

- Enhetstester
- Integrasjonstester
- Ende-til-ende-tester

---

### Hvorfor tester man?

- Verifisere korrekthet
- Unngå regresjon
- CI/CD
- Dokumentere oppførsel

---

### Tester i backend vs i frontend

- Typisk mye mer tester i backend
- Backend: mer forretningslogikk, kompleksitet
- Frontend: hyppigere endringsrate

---

### Testing er en avveining

- Testing tar utviklingstid
- Dårlige tester kan senke utviklingshastighet
- Prioriter! Risiko = konsekvenser $\times\$ sannsynlighet

---

### Test-landskapet i frontend

- Kodekvalitetsverktøy
- Jest: Enhetstesting
- Vue testing library: Teste Vue-komponenter
- Cypress: Ende-til-ende tester

---

### Kodekvalitetsverktøy

- De beste testene er de du aldri trenger å skrive
- Typesikkerhet med Typescript
- Linting med ESLint
- Kodeformatering med Prettier

---

### Enhetstesting med Jest

- Funksjoner, utregninger, algoritmer, utilities
- _Pure_ functions ❤️

---

### Enhetstesting med Jest

```TS
function calculateMean(values: number[]): number {
  const sum = values.reduce((a, b) => a + b)

  return sum / values.length
}

test("can calculate mean of array", () => {
  expect(calculateMean([1, 2, 3])).toEqual(6)
});
```

---

### Vue Testing Library

- Teste oppførselen til Vue-komponenter
- Interagere med komponenten: Trykke på knapper, skrive inn tekst
- Props + state ➡️ DOM-elementer
- Eller...
- Props + handlinger ➡️ DOM-elementer

---

### Vue Testing Library

```VUE
<template>
  <div>
    <p>Times clicked: {{ count }}</p>
    <button @click="increment">increment</button>
  </div>
</template>

<script>
export default {
  data: () => ({
    count: 0,
  }),

  methods: {
    increment() {
      this.count++;
    },
  },
};
</script>
```

---

```JS
test('increments value on click', async () => {
  const { getByText } = render(Component)

  getByText('Times clicked: 0')

  const button = getByText('increment')

  await userEvent.click(button)
  await userEvent.click(button)

  getByText('Times clicked: 2')
})

```

---

### Cypress

- Ende-til-ende-tester (blant annet)
- Tester en nettside i nettleseren
- Kan teste alt en bruker kan teste
- Mye verdi for lite testkode

---

### Cypress

```JS
describe('A group of tests...', () => {
  it('Can load front page', () => {
    cy.visit('/');

    cy.contains('h1', 'Hello world').should("exist");
  });
});

```

---

### Cypress demo

🚀

---

### Cypress og CI/CD

- Kan kjøre Cypress-tester i bygge-pipeline
  - Github action ➡️ docker-compose up ➡️ e2e-tester
- Kan kjøre Cypress-tester i dev/test-miljø etter deploy

---

### Oppsummering

- Hvor mye skal man vektlegge frontend-testing?
- Reduser test-kompleksitet, og ikke test implementasjon
- Ende-til-ende tester gir mye verdi for lite testkode

---

### Spørsmål ❓

---

### Oppgaver

- Utgangspunkt i membership-system-repoet
- Sjekk ut følgende branch: https://github.com/NTNUI/membership-system/tree/frontend-testing
- Oppgaver i Cypress.md
