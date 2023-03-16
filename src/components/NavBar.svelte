<script>
    import Logo from "./Logo.svelte";
</script>

<div class="absolute w-full whitespace-nowrap">
    <div class="flex flex-row h-20 border-b border-neutral-200 bg-white py-3 px-5 justify-between">
        <div class="flex flex-row gap-4 w-full h-full items-center">
            <Logo />
            <span class="text-sky-700 text-xl font-semibold">Aplikasi Cek STNK </span>
        </div>

        <div class="flex flex-row gap-3 h-full items-center font-semibold">
            <a href="/" class="hover:text-sky-600">Beranda</a>
<!--            <a href="" class="hover:text-sky-600">Tentang Kami</a>-->
        </div>
    </div>
</div>

