<template>
   <div
          class="alert alert col-2 m-0"
          role="alert"
          :style="'background:' + info.color + '; color: #2c3e50'"
        >
          <h4>
            <strong>
              {{ sheet.info.name }}
              <br />
              <h5>({{ info.player }})</h5>
              <br />
			  
              <h5>
                {{ info.nature.name }}/{{ info.demeanor.name }}
              </h5>
            </strong>
          </h4>
        </div>
</template>

<script>
export default {
  name: 'Header',
  props: {
    info: Object
  }
}
</script>
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
          }
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
