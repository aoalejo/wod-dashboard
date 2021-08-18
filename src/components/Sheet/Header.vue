<template>
  <b-alert
    class="p-0 m-0 h-100"
    align-self="stretch"
    show
    :style="'background: ' + info.color"
  >
    <h3>
      <b-badge
        variant="light"
        class="m-2 d-flex flex-fill text-center justify-content-center"
        v-b-modal="'HeaderSheetModal' + info.color + info.name"
      >
        <strong>
          {{ info.name }}
        </strong>
        <b-modal
          size="lg"
          hide-backdrop
          :id="'HeaderSheetModal' + info.color + info.name"
        >
          <template #modal-header="{}" class="p-0 m-0">
            <!-- Emulate built in modal header close button action -->
            <div class="p-0 m-0" />
          </template>

          <FeaturesPopup
            class="col-12 m-0 p-0"
            :color="sheet.info.color"
            :abilities="sheet.abilities"
            :attributes="sheet.attributes"
            :advantages="sheet.advantages"
            :sheet="sheet"
          />
        </b-modal>
      </b-badge>
    </h3>
    <h5>
      <b-badge
        variant="light"
        class="m-2 d-flex flex-fill text-center justify-content-center"
      >
        {{ info.player }}
      </b-badge>
    </h5>

    <div class="row d-flex m-1">
      <b-badge
        class="flex-fill m-1"
        v-for="(val, index) in info.values"
        :key="'HeaderInfo' + index + info.color + info.name"
        v-b-popover.hover.top="
          val.description.length > 200
            ? val.description.slice(0, 200) + '... (click para ver completo)'
            : val.description.slice(0, 200)
        "
        v-b-modal="'HeaderInfoModal' + index + info.color + info.name"
        :title="val.type + ': ' + val.name"
      >
        {{ val.name }}
        <b-modal
          size="xl"
          hide-backdrop
          :id="'HeaderInfoModal' + index + info.color + info.name"
          >{{ val.description }}</b-modal
        >
      </b-badge>
    </div>
  </b-alert>
</template>
  "values": [
      {
        "type": "Naturaleza",
        "name": "Bellaco",
        "description": "Al Bellaco sólo le importa una cosa: él mismo. A cada uno lo suyo, y si los demás son incapaces de protegerse es su problema. No tiene por qué tratarse de un matón; simplemente se niega a someterse a los caprichos de los demás. Prácticamente todos los Bellacos se creen autosuficientes y tienen sus propios intereses siempre presentes. Las prostitutas, capitalistas y criminales encarnan bien este Arquetipo. Entre los Vástagos Bellacos se incluyen diabolistas, Autarkis y un Primogénito que pone los intereses de su Clan por encima del conjunto del resto de la Estirpe. —Recupera un punto de Fuerza de Voluntad cuando tu actitud egoísta te conduzca a una gran ganancia material o de cualquier otro tipo. A discreción del Narrador, acumular ganancias sin exponer tus debilidades debería permitirte ganar dos puntos. Además también puedes recuperar un punto de Fuerza de Voluntad cuando tus esfuerzos beneficien al grupo al que perteneces cuando el beneficio se produzca a costa de otro grupo."
      },
      {
        "type": "Conducta",
        "name": "Enigma",
        "description": "Tus actos son incomprensibles, extraños e inexplicables para todos excepto para ti mismo. Tu rareza puede ser un efecto residual de tu Abrazo o el modo más efectivo de cumplir tus personalidades. Sin embargo para el resto del mundo tu comportamiento errático sugiere que eres un excéntrico, si es que no estás completamente loco. Los teóricos de la conspiración, los agentes encubiertos y los fanáticos de la Yihad poseen este Arquetipo. Los Vástagos Enigmáticos a menudo han sufrido algún tipo de herida o trauma que intentan curar, o simplemente utilizan su comportamiento para ocultar algo más profundo. —Recuperas un punto de Fuerza de Voluntad cada vez que alguien queda totalmente perplejo ante una acción tuya que termina siendo provechosa."
      },
      {
        "type": "Concepto",
        "name": "Detective Privado",
        "description": "detective, policía de paisano, agente gubernamental, detective privado, cazador de brujas"
      },
      {
        "type": "Clan",
        "name": "Malkavian",
        "description": "a malkavian description"
      },
      {
        "type": "Generación",
        "name": "8 va",
        "description": "a 8 gen description"
      },
      {
        "type": "Sire",
        "name": "Elisabeth Piltz",
        "description": "a Elisabeth Piltz description"
      },
      {
        "type": "Debilidad",
        "name": "Esquizofrenia",
        "description": "La esquizofrenia es un trastorno mental grave por el cual las personas interpretan la realidad de manera anormal. La esquizofrenia puede provocar una combinación de alucinaciones, delirios y trastornos graves en el pensamiento y el comportamiento, que afecta el funcionamiento diario y puede ser incapacitante."
      }
    ]
  },
<script>
import FeaturesPopup from "./FeaturesPopup.vue";

export default {
  components: { FeaturesPopup },
  name: "Header",
  props: {
    info: Object,
    sheet: Object,
  },
};
</script>
<style scoped>
.badge {
  overflow: hidden;
  text-overflow: ellipsis;
}
.alert {
  border-top-left-radius: 0.25rem;
  border-bottom-left-radius: 0.25rem;
  border-bottom-right-radius: 0rem;
  border-top-right-radius: 0rem;
}
</style>
