<template>
  <div class="row justify-content-center">
    <div class="col-8">
      <form name="editForm" role="form" novalidate v-on:submit.prevent="save()">
        <h2
          id="farmaciaApp.laboratorio.home.createOrEditLabel"
          data-cy="LaboratorioCreateUpdateHeading"
          v-text="$t('farmaciaApp.laboratorio.home.createOrEditLabel')"
        >
          Create or edit a Laboratorio
        </h2>
        <div>
          <div class="form-group" v-if="laboratorio.id">
            <label for="id" v-text="$t('global.field.id')">ID</label>
            <input type="text" class="form-control" id="id" name="id" v-model="laboratorio.id" readonly />
          </div>
          <div class="form-group">
            <label class="form-control-label" v-text="$t('farmaciaApp.laboratorio.nombre')" for="laboratorio-nombre">Nombre</label>
            <input
              type="text"
              class="form-control"
              name="nombre"
              id="laboratorio-nombre"
              data-cy="nombre"
              :class="{ valid: !$v.laboratorio.nombre.$invalid, invalid: $v.laboratorio.nombre.$invalid }"
              v-model="$v.laboratorio.nombre.$model"
              required
            />
            <div v-if="$v.laboratorio.nombre.$anyDirty && $v.laboratorio.nombre.$invalid">
              <small class="form-text text-danger" v-if="!$v.laboratorio.nombre.required" v-text="$t('entity.validation.required')">
                This field is required.
              </small>
            </div>
          </div>
        </div>
        <div>
          <button type="button" id="cancel-save" data-cy="entityCreateCancelButton" class="btn btn-secondary" v-on:click="previousState()">
            <font-awesome-icon icon="ban"></font-awesome-icon>&nbsp;<span v-text="$t('entity.action.cancel')">Cancel</span>
          </button>
          <button
            type="submit"
            id="save-entity"
            data-cy="entityCreateSaveButton"
            :disabled="$v.laboratorio.$invalid || isSaving"
            class="btn btn-primary"
          >
            <font-awesome-icon icon="save"></font-awesome-icon>&nbsp;<span v-text="$t('entity.action.save')">Save</span>
          </button>
        </div>
      </form>
    </div>
  </div>
</template>
<script lang="ts" src="./laboratorio-update.component.ts"></script>
