<script lang="ts">
    const objects = ['airplane', 'car', 'drawer', 'orange', 'sand'];
    const editedExtension = '-edited';
    const base_img_path = 'imgs/';
    const object_filenames = objects.map((object) => base_img_path + object + '.png');
    const object_filenames_edited = objects.map((object) => base_img_path + object + editedExtension + '.jpeg');
</script>
{#each objects as object, i}
    <div>
        <img src={object_filenames[i]} alt={object} />
        <img src={object_filenames_edited[i]} alt={object} />
    </div>
{/each}
