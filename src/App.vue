<script>
export default {
  data() {
    return {
      nombre: '',
      nombreState: null,
      apellido: '',
      nombreState: null,
      cp: '',
      cpState: null,
      calle: '',
      calleState: null,
      numero: '',
      numeroState: null,
      ciudad: '',
      ciudadState: null,
      fecha: '',
      fechaState: null,
      email: '',
      emailState: null,
      numeroTel: '',
      numeroTelState: null,
    };
  },
  methods: {
    validateNombre() {
      this.nombreState = this.nombre.length > 0 || this.nombre != 'Nombre' ? true : false;
    },
    validateApellido() {
      this.apellidoState = this.apellido.length > 0 ? true : false;
    },
    validateDireccion() {
      this.cpState = this.cp.length > 0 ? true : false;
      this.calleState = this.calle.length > 0 ? true : false;
      this.numeroState = this.numero.length > 0 ? true : false;
      this.ciudadState = this.ciudad.length > 0 ? true : false;
    },
    validateFecha() {
      //FECHA MAYOR DE 18
      this.fechaState = this.fecha.length != null ? true : false;
    },
    validateEmail() {
      //VERIFICAR QUE SEA EMAIL
      this.emailState = this.email.length > 0 ? true : false;
    },
    validateNumeroTel() {
      //VERIFICAR QUE SEA EMAIL
      this.numeroTelState = this.numeroTel.length > 0 ? true : false;
    },
    chooseImage() {
      this.$refs.fileInput.click()
    },
    handleSubmit() {
      if (this.nombreState == null) {
        alert("Debes de rellenar todos los campos")
      } else {
        alert("Se mando")
      }
    },

  },
}

</script>

<template>
  <div>
    <header>
      <div>
        <b-navbar type="dark" variant="dark">
          <b-navbar-brand href="#">
            Marco Rayo
          </b-navbar-brand>
        </b-navbar>
      </div>
    </header>
    <div class="container">
      <div>
        <h1 class="text-center">
          Validación Formulario
        </h1>
      </div>
      <div class="col-md-8 mx-auto rounded" style="background-color: whitesmoke;">
        <div class="col-md-10 mx-auto">
          <b-form @submit.prevent="handleSubmit()">
            <!--NOMBRE-->
            <div class="row col-md-12 mx-auto">
              <b-form-group label-for="input-nombre" :state="nombreState" style="padding-top: 2rem;">
                <b-form-input id="input-nombre" v-model="nombre" :state="nombreState" @input="validateNombre()"
                  placeholder="Nombre"></b-form-input>
                <b-form-invalid-feedback :state="nombreState">
                  El nombre es obligatorio.
                </b-form-invalid-feedback>
              </b-form-group>
            </div>

            <!--APELLIDOS-->
            <b-form-group label-for="input-apellido" :state="apellidoState" style="padding-top: 1rem;">
              <div class="row col-md-12 mx-auto">
                <div class="col-md-6">
                  <b-form-input id="apellido-nombre" v-model="apellido" :state="apellidoState" @input="validateApellido"
                    placeholder="Apellido Paterno"></b-form-input>
                </div>
                <div class="col-md-6">
                  <b-form-input id="apellidoMaterno" v-model="apellidoMaterno"
                    placeholder="Apellido Materno"></b-form-input>
                </div>
              </div>
              <b-form-invalid-feedback :state="apellidoState">
                El apellido paterno es obligatorio.
              </b-form-invalid-feedback>
            </b-form-group>

            <!--DIRECCION-->
            <b-form-group label-for="input-direccion" style="padding-top: 1rem;">
              <div class="row col-md-12 mx-auto">
                <div class="col-md-4">
                  <!--NUMERO-->
                  <b-form-input id="cp" v-model="cp" type="number" :state="cpState" @input="validateDireccion"
                    placeholder="Código Postal"></b-form-input>
                </div>
                <div class="col-md-3">
                  <b-form-input id="calle" v-model="calle" :state="calleState" @input="validateDireccion"
                    placeholder="Calle"></b-form-input>
                </div>
                <div class="col-md-2">
                  <!--NUMERO-->
                  <b-form-input id="numero" v-model="numero" type="number" :state="numeroState" @input="validateDireccion"
                    placeholder="#">
                  </b-form-input>
                </div>
                <div class="col-md-3">
                  <b-form-input id="ciudad" v-model="ciudad" :state="ciudadState" @input="validateDireccion"
                    placeholder="Ciudad"></b-form-input>
                </div>
              </div>
              <b-form-invalid-feedback :state="ciudadState">
                La dirección es obligatoria.
              </b-form-invalid-feedback>
            </b-form-group>

            <!--FECHA NACIMIENTO-->
            <div class="row col-md-12 mx-auto">
              <b-form-group label-for="input-fecha" :state="fechaState" style="padding-top: 1rem;">
                <b-form-input id="input-fecha" v-model="fecha" type="date" :state="fechaState" @input="validateFecha"
                  placeholder="Fecha de Nacimiento"></b-form-input>
                <b-form-invalid-feedback :state="fechaState">
                  La fecha es obligatoria.
                </b-form-invalid-feedback>
              </b-form-group>
            </div>

            <!--EMAIL-->
            <div class="row col-md-12 mx-auto">
              <b-form-group label-for="input-email" :state="emailState" style="padding-top: 1rem;">
                <b-form-input id="input-email" v-model="email" type="email" :state="emailState" @input="validateEmail"
                  placeholder="Correo Electrónico"></b-form-input>
                <b-form-invalid-feedback :state="emailState">
                  El email es obligatorio.
                </b-form-invalid-feedback>
              </b-form-group>
            </div>

            <!--NUM-->
            <div class="row col-md-12 mx-auto">
              <b-form-group label-for="input-numero" :state="numeroTelState" style="padding-top: 1rem;">
                <b-form-input id="input-numero" v-model="numeroTel" type="number" :state="numeroTelState"
                  @input="validateNumeroTel" placeholder="Número Telefónico"></b-form-input>
                <b-form-invalid-feedback :state="numeroTelState">
                  El número es obligatorio.
                </b-form-invalid-feedback>
              </b-form-group>
            </div>

            <!--IMG-->
            <div class="row col-md-12 mx-auto">
              <b-form-group label-for="input-img" :state="imgState" style="padding-top: 1rem;">
                <div class="image-input"  @click="chooseImage">                  
                  <input class="file-input" ref="fileInput" type="file" @input="onSelectFile">
                </div>                
              </b-form-group>
            </div>                    

            <!--BOTON-->
            <b-form-group class="col-md-2 mx-auto" style="padding-top: 0.5rem;">
              <b-button type="submit" class="btn btn-success">Enviar</b-button>
            </b-form-group>
          </b-form>
          <!--                            
          <b-form @submit.stop.prevent>
            <label for="nombre" style="padding-top: 0.5rem;">Nombre</label>
            <b-form-input v-model="nombreId" :state="validation" id="nombre"></b-form-input>
            <label>Apellido</label>
            <div class="input-group">              
              <input type="text" class="form-control" placeholder="Paterno">
              <input type="text" class="form-control" placeholder="Materno">
            </div>
            <label for="nombre">Dirección</label>
            <div class="input-group">              
              <input type="number" class="form-control" placeholder="CP">
              <input type="text" class="form-control" placeholder="Calle">
              <input type="number" class="form-control" placeholder="#">
              <input type="text" class="form-control" placeholder="Ciudad">
            </div>
            <label for="nombre">Fecha Nacimiento</label>
            <b-form-input v-model="naciminetoId" :state="validation" id="nacimiento" type="date"></b-form-input>
            <label for="nombre">Email</label>
            <b-form-input v-model="emailId" :state="validation" id="email" type="email"></b-form-input>
            <label for="nombre">Número telefónico</label>
            <b-form-input v-model="numeroId" :state="validation" id="numero" type="tel"></b-form-input>
            <label for="nombre">Fotografía</label>
            <b-form-input v-model="fotoId" :state="validation" id="foto" type="file"></b-form-input>
            <div class="col-md-4 mx-auto" style="padding-top: 0.5rem; padding-bottom: 0.5rem;"> 
              <button class="btn btn-success" type="submit">Enviar</button>
            </div>            
          </b-form>
          -->
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
