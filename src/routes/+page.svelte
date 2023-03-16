<script>
    let searching = false;
    let value = '';
    let results = [];
    let comp;
    let cover = 'https://previews.123rf.com/images/balabolka/balabolka2008/balabolka200800112/154494975-cartoon-cute-doodles-vehicle-frame-card-line-art-detailed-with-lots-of-objects-background-all-object.jpg';

    function highlight(text) {
        const regex = new RegExp(String(value).trim(), 'gi');
        return String(text).replace(regex, match => {
            return `<strong class="text-sky-600">${match}</strong>`;
        });
    }

    function executing(e) {
        if ((e.keyCode === 13 || e.keyCode === undefined) && value.trim().length > 0) {
            search();
        }
    }

    function search() {
        searching = true;
        const searchParam = value.trim();

        fetch(`http://localhost:1337/api/cek-stnks?filters[$or][0][nomor_rangka][$containsi]=${searchParam}&filters[$or][1][nama_customer][$containsi]=${searchParam}`, {
            method: 'GET',
            headers: {'Content-Type': 'application/json',}
        })
            .then(async response => {
                const {data} = await response.json();
                results = [...data];
                comp.blur()
                searching = false;
            })
            .catch(error => {
                searching = false;
            })
    }
</script>
<div class="flex flex-col gap-6 whitespace-nowrap px-12 h-fit">
    <div class="flex flex-col items-center w-full ">
        <span class="text-lg text-sky-700">Masukan Nomor STNK atau Nama Pemilik Kendaraan</span>
    </div>
    <div class="flex flex-col w-full group items-center">
        <div class="relative w-full md:w-1/2">
            <!--            disable blocker-->
            {#if searching}
                <div class="absolute h-12 w-full rounded-lg bg-gray-200 opacity-50"></div>
            {/if}
        </div>
        <div class="bg-white flex flex-row outline outline-1 rounded-lg outline-sky-200 group-focus:outline-sky-500 w-full md:w-1/2">
            <input on:keyup={executing} bind:this={comp}
                   class="w-full h-12 rounded-lg outline outline-0 outline-sky-200 focus:outline-sky-500 px-4"
                   type="text" bind:value={value}/>
            <button disabled={value.trim().length <= 0} on:click={executing}
                    class="px-6 py-1 disabled:bg-sky-200 bg-sky-400 rounded-r-lg text-white">Cari
            </button>
        </div>
        <div class="flex flex-col items-end py-6 w-full items-center">
            <span class="text-sm">INFORMASI WAKTU PENGAMBILAN STNK, PLAT & BPKB UNIT KENDARAAN <a href="" class="text-sky-600">Klik Disini</a></span>
<!--            <span class="text-xs"></span>-->
        </div>
    </div>

    <!--    Result-->
    <div class="flex flex-col gap-6 items-center">

        {#each results as {attributes}}
            <div class="rounded-lg overflow-hidden border border-neutral-300 bg-white w-full md:w-1/2">
<!--                <div class="w-full h-52 ">-->
<!--                    <img class="w-full h-full object-cover" src={cover}-->
<!--                         alt="Sunset in the mountains">-->
<!--                </div>-->
                <div class="px-6 py-4">
                    <div class="font-bold text-xl mb-2">
                        {@html highlight(attributes.nama_customer)}
                    </div>
                    <p class="text-gray-700 text-base">
                        {attributes.type}
                    </p>
                    <p class="text-gray-700 text-base">
                        {@html highlight(attributes.nomor_rangka)}
                    </p>
                    <p class="text-gray-700 text-base">
                        {attributes.nomor_polisi}
                    </p>
                    <p class="text-gray-700 text-base">
                        STNK: {attributes.stnk ? 'Ada' : 'Tidak Ada'}
                    </p>
                    <p class="text-gray-700 text-base">
                        PLAT: {attributes.plat ? 'Ada' : 'Tidak Ada'}
                    </p>
                    <p class="text-gray-700 text-base">
                        BPKB: {attributes.stnk ? 'Ada' : 'Tidak Ada'}
                    </p>
                    <p class="text-gray-700 text-base">
                        Faktur Pemilik: {attributes.f_pemilik ? 'Ada' : 'Tidak Ada'}
                    </p>
                </div>
<!--                <div class="px-6 pt-4 pb-2">-->
<!--                    {#if attributes.stnk}-->
<!--                        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold bg-teal-500 text-white mr-2 mb-2">stnk</span>-->
<!--                    {/if}-->
<!--                    {#if attributes.plat}-->
<!--                        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold bg-orange-300 text-white mr-2 mb-2">plat</span>-->
<!--                    {/if}-->
<!--                    {#if attributes.plat}-->
<!--                        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold bg-purple-400 text-white mr-2 mb-2">bpkb</span>-->
<!--                    {/if}-->
<!--                    {#if attributes.f_pemilik}-->
<!--                        <span class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold bg-gray-400 text-white mr-2 mb-2">f pemilik</span>-->
<!--                    {/if}-->
<!--                </div>-->
            </div>
        {/each}


        <div></div>

    </div>
</div>
