# Custom bootstrap mit webpack
https://www.devextent.com/npm-compile-sass/

https://getbootstrap.com/docs/5.0/getting-started/webpack/


Damit bootstrap modal global verwendbar wird, muss expose loader installiert sein.



```
// src/js/custom_bootstrap.js:

//import Modal from 'bootstrap/js/dist/modal';
import { BootstrapModal } from "expose-loader?exposes=BootstrapModal!../../node_modules/bootstrap/js/dist/modal";
```

index.html:
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8"/>
	<title>Getting Started</title>
	<link rel="stylesheet" href="css/custom_bootstrap.css">
	<script src="js/custom_bootstrap.js"></script>
</head>
<body>
<!-- Button trigger modal -->
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">
	Launch demo modal
</button>


<button id="myButton" class="btn btn-primary">Open Bootstrap Modal</button>
<script>
    /** Open modal programmatically **/
    document.getElementById('myButton').addEventListener('click', function (event) {
        /** BootstrapModal is located in the global scope thanks to expose-loader **/
        let modal = new BootstrapModal(document.getElementById('exampleModal'));
        modal.show();
    });
</script>

<!-- Modal -->
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
	<div class="modal-dialog">
		<div class="modal-content">
			<div class="modal-header">
				<h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
				<button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
			</div>
			<div class="modal-body">
				...
			</div>
			<div class="modal-footer">
				<button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
				<button type="button" class="btn btn-primary">Save changes</button>
			</div>
		</div>
	</div>
</div>
</body>
</html>

```

