<script lang="ts">
    function toTitleCase(str: string) {
        return str.replace(/\w\S*/g, function (txt: string) {
            return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
        });
    }

    const objects = ["airplane", "car", "drawer", "orange", "sand"];
    const editedExtension = "-edited";
    const base_img_path = "imgs/";
    const object_filenames = objects.map(
        (object) => base_img_path + object + ".jpeg",
    );
    const object_filenames_edited = objects.map(
        (object) => base_img_path + object + editedExtension + ".jpeg",
    );

    let objectState = objects.map(() => false);
</script>

<div class="p-5">
    <div class="grid grid-cols-2 md:grid-cols-3 gap-5">
        {#each objects as object, i}
            <div>
                <button on:click={() => (objectState[i] = !objectState[i])}>
                    <p class="text-white">
                        {objectState[i] ? "Light" : "Dark"}
                        {toTitleCase(object)}
                    </p>
                        {#if objectState[i]}
                            <img
                                src={object_filenames_edited[i]}
                                alt={object}
                                class="h-auto max-w-full rounded-lg shadow shadow-2xl shadow-neutral-900"
                            />
                        {:else}
                            <img
                                src={object_filenames[i]}
                                alt={object}
                                class="h-auto max-w-full rounded-lg shadow shadow-2xl shadow-neutral-900"
                            />
                        {/if}
                </button>
            </div>
        {/each}
    </div>
</div>
