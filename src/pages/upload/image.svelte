
<script>
      document.addEventListener('paste', function (evt) {
                    const clipboardItems = evt.clipboardData.items;
                    const items = [].slice.call(clipboardItems).filter(function (item) {
                        // Filter the image items only
                        return item.type.indexOf('image') !== -1;
                    });
                    if (items.length === 0) {
                        return;
                    }

                    const item = items[0];
                    const blob = item.getAsFile();

                    const imageEle = document.getElementById('preview');
                    imageEle.src = URL.createObjectURL(blob);
                });
</script>
<div class="container">
    <div>
        <div><kbd class="key">Ctrl</kbd> + <kbd class="key">V</kbd> in this window.</div>
        <img class="preview" id="preview" />
<form  method="POST">
<button type="submit" id="upload">Upload</button>
</form>
    </div>
</div>