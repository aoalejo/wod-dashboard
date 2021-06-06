<template>
  <div class="sheets">
    <b-card class="d-flex m-2" no-body>
      <b-card
        class="m-2 p-0 flex-fill"
        v-for="(sheet, index) in sheets"
        :key="'sheet' + index"
        head
        no-body
      >
       <Header info/>
      </b-card>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "Sheets",
  data: function() {
    return {
      roll: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0],
      rolls: [],
      columns: ["Atuel - Karl"],
      sheets: [
        {
          info: {
            name: "Karl",
            player: "Atuel",
            color: "#19a3a6",
            nature: {
              name: "Bellaco",
              description:
                "Al Bellaco sólo le importa una cosa: él mismo. A cada uno lo suyo, y si los demás son incapaces de protegerse es su problema. No tiene por qué tratarse de un matón; simplemente se niega a someterse a los caprichos de los demás. Prácticamente todos los Bellacos se creen autosuficientes y tienen sus propios intereses siempre presentes. Las prostitutas, capitalistas y criminales encarnan bien este Arquetipo. Entre los Vástagos Bellacos se incluyen diabolistas, Autarkis y un Primogénito que pone los intereses de su Clan por encima del conjunto del resto de la Estirpe. —Recupera un punto de Fuerza de Voluntad cuando tu actitud egoísta te conduzca a una gran ganancia material o de cualquier otro tipo. A discreción del Narrador, acumular ganancias sin exponer tus debilidades debería permitirte ganar dos puntos. Además también puedes recuperar un punto de Fuerza de Voluntad cuando tus esfuerzos beneficien al grupo al que perteneces cuando el beneficio se produzca a costa de otro grupo.",
            },
            demeanor: {
              name: "Enigma",
              description:
                "Tus actos son incomprensibles, extraños e inexplicables para todos excepto para ti mismo. Tu rareza puede ser un efecto residual de tu Abrazo o el modo más efectivo de cumplir tus personalidades. Sin embargo para el resto del mundo tu comportamiento errático sugiere que eres un excéntrico, si es que no estás completamente loco. Los teóricos de la conspiración, los agentes encubiertos y los fanáticos de la Yihad poseen este Arquetipo. Los Vástagos Enigmáticos a menudo han sufrido algún tipo de herida o trauma que intentan curar, o simplemente utilizan su comportamiento para ocultar algo más profundo. —Recuperas un punto de Fuerza de Voluntad cada vez que alguien queda totalmente perplejo ante una acción tuya que termina siendo provechosa.",
            },
            concept: {
              name: "Detective Privado",
              description:
                "detective, policía de paisano, agente gubernamental, detective privado, cazador de brujas",
            },
            clan: "Malkavian",
            generation: "8",
            sire: "Elisabeth Piltz",
            weakness: "",
          },
          attributes: {
            physical: {
              strenght: 2,
              dextery: 4,
              stamina: 2,
            },
            social: {
              charisma: 5,
              manipulation: 2,
              appearance: 3,
            },
            mental: {
              perception: 2,
              intelligence: 13,
              wits: 3,
            },
          },
          virtues: {
            conscience: 3,
            selfControl: 4,
            courage: 4,
          },
          points: [
            {
              name: "Habilidades",
              categories: [
                {
                  name: "Talentos",
                  values: [
                    {
                      name: "Alerta",
                      value: 2,
                    },
                    {
                      name: "Atletismo",
                      value: 1,
                    },
                    {
                      name: "Callejeo",
                      value: 1,
                    },
                    {
                      name: "Consciencia",
                      value: 0,
                    },
                    {
                      name: "Empatía",
                      value: 2,
                    },
                    {
                      name: "Expresión",
                      value: 0,
                    },
                    {
                      name: "Intimidación",
                      value: 3,
                    },
                    {
                      name: "Liderazgo",
                      value: 0,
                    },
                    {
                      name: "Pelea",
                      value: 2,
                    },
                    {
                      name: "Subterfugio",
                      value: 2,
                    },
                    {
                      name: "...",
                      value: 0,
                    },
                    {
                      name: "...",
                      value: 0,
                    },
                  ],
                },
                {
                  name: "Técnicas",
                  values: [
                    {
                      name: "Armas de Fuego",
                      value: 3,
                    },
                    {
                      name: "Artesanía",
                      value: 0,
                    },
                    {
                      name: "Conducir",
                      value: 1,
                    },
                    {
                      name: "Etiqueta",
                      value: 1,
                    },
                    {
                      name: "Interpretación",
                      value: 3,
                    },
                    {
                      name: "Latrocinio",
                      value: 0,
                    },
                    {
                      name: "Pelea con Armas",
                      value: 0,
                    },
                    {
                      name: "Sigilo",
                      value: 3,
                    },
                    {
                      name: "Supervivencia",
                      value: 0,
                    },
                    {
                      name: "T.c. Animales",
                      value: 0,
                    },
                    {
                      name: "...",
                      value: 0,
                    },
                    {
                      name: "...",
                      value: 0,
                    },
                  ],
                },
                {
                  name: "Conocimientos",
                  values: [
                    {
                      name: "Academicismo",
                      value: 0,
                    },
                    {
                      name: "Ciencias",
                      value: 0,
                    },
                    {
                      name: "Finanzas",
                      value: 0,
                    },
                    {
                      name: "Informática",
                      value: 0,
                    },
                    {
                      name: "Investigación",
                      value: 3,
                    },
                    {
                      name: "Leyes",
                      value: 0,
                    },
                    {
                      name: "Medicina",
                      value: 1,
                    },
                    {
                      name: "Ocultismo",
                      value: 0,
                    },
                    {
                      name: "Política",
                      value: 1,
                    },
                    {
                      name: "Tecnología",
                      value: 1,
                    },
                    {
                      name: "...",
                      value: 0,
                    },
                    {
                      name: "...",
                      value: 0,
                    },
                  ],
                },
              ],
            },
            {
              name: "Ventajas",
              categories: [
                {
                  name: "Disciplinas",
                  values: [
                    {
                      name: "Ofuscación",
                      value: 1,
                    },
                    {
                      name: "Dementación",
                      value: 2,
                    },
                  ],
                },
                {
                  name: "Trasfondos",
                  values: [
                    {
                      name: "Generación",
                      value: 5,
                      description:
                        "lo alejado que se encuentra el personaje de Caín",
                    },
                    {
                      name: "Rebaño",
                      value: 1,
                      description:
                        "los recipientes a los que el personaje tiene acceso libre y seguro.",
                    },
                    {
                      name: "Aliados",
                      value: 3,
                      description:
                        "compañeros humanos, normalmente familiares o amigos.",
                    },
                    {
                      name: "Recursos",
                      value: 1,
                      description:
                        "riquezas, pertenencias e ingresos del personaje.",
                    },
                  ],
                },
              ],
            },
          ],
          merits: [
            {
              name: "Cara Amistosa",
              cost: 1,
              description:
                "Tienes una cara que a todo el mundo le recuerda a alguien, hasta el punto que los extraños se ven inclinados a tu favor por ello. El efecto no se desvanece incluso si explicas su “error”, lo que te proporciona un –1 a la dificultad en todas las tiradas Sociales apropiadas (válido para Seducción, por ejemplo, pero no para Intimidación) cuando hay un extraño. Este Mérito sólo funciona la primera vez que te encuentras con alguien.",
            },
            {
              name: "Idioma",
              cost: 1,
              description:
                "Conoces un idioma además de tu lengua materna. Puedes adquirir este Mérito varias veces, cada vez para un idioma diferente.",
            },
          ],
          defects: [],
          path: {
            name: "Humanidad",
            value: {
              max: 7,
              now: 7,
            },
            bearing: {
              name: "Normalidad",
              value: 0,
            },
          },
          willpower: {
            value: {
              max: 8,
              now: 8,
            },
          },
          bloodpool: {
            bloodPerTurn: 3,
            value: {
              max: 18,
              now: 18,
            },
          },
          health: {
            max: 7,
            damage: ["non-letal"],
          },
        },
      ],
    };
  },
  mounted() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
