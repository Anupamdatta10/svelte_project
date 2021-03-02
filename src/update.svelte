<script>
  
   let name;
   let age;
  export let modal_id;
</script>

<div
  class="modal fade"
  id={modal_id}
  tabindex="-1"
  role="dialog"
  aria-labelledby="exampleModalCenterTitle"
  aria-hidden="true"
>
  <div class="modal-dialog modal-dialog-centered" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLongTitleupdate">
          Add data in table
        </h5>
        <button
          type="button"
          class="close"
          data-dismiss="modal"
          aria-label="Close"
        >
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <div class="form-group">
          <label for="input_name" class="col-form-label">name</label>
          <input
            class="form-control"
            id="update_name"
            type="text"
            bind:value={name}
          />
        </div>
        <div class="form-group">
          <label for="input_age" class="col-form-label">age</label>
          <input
            class="form-control"
            id="update_age"
            type="text"
            bind:value={age}
          />
        </div>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal"
          >Close</button
        >
        <button
          type="button"
          class="btn btn-primary"
          data-dismiss="modal"
         >Save changes</button
        >
      </div>
    </div>
  </div>
</div>
