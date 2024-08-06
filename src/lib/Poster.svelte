<script>
        export let background = 'default';
        export let width = '300px';
    </script>

<div style="width: {width}; box-shadow: 0 0 20px rgba(0, 0, 0, 0.15); position: relative; border-radius: 5px; height: 200px; display: flex; background: {background}">
    <slot></slot>
</div>