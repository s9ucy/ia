<script>
	var typed = "";
	var incorrect = "";
	var untyped =
		"We're no strangers to love you know the rules and so do I A full commitment's what I'm thinking of";
	var untyped_orig = untyped;
	var key;
	var keyCode;

	function handleKeydown(event) {
		key = event.key;
		keyCode = event.KeyCode;
		if (key == "Tab") {
			typed = "";
			incorrect = "";
			untyped = untyped_orig;
		} else if (key == "Shift") {
			pass;
		} else if (key == "Control") {
			pass;
		} else if (key == "Alt") {
			pass;
		} else if (key == untyped.charAt(0)) {
			typed = typed + key;
			untyped = untyped.slice(1, untyped.length);
		} else if (key == "Backspace") {
			incorrect = incorrect.slice(0, incorrect.length - 1);
		} else {
			if (untyped.charAt(0) == " ") {
				incorrect = incorrect + key;
			} else {
				incorrect = incorrect + untyped.charAt(0);
				untyped = untyped.slice(1, untyped.length);
			}
		}
	}
</script>

<svelte:window on:keydown|preventDefault={handleKeydown} />
<div class="myDiv">
	<h1 class="letest">
		{typed}<span style="color:red;">{incorrect}</span><span
			style="color:grey;">{untyped}</span
		>
	</h1>
</div>

<style>
	.myDiv {
		background-color: pink;
		margin: auto;
		width: 60%;
		text-align: center;
		height: 400px;
	}

	.letest {
		color: white;
		font-family: "Roboto Mono", monospace;
		font-size: 30px;
	}
</style>
