<script>
    import Wa from "./Wa.svelte";
    import Ig from "./Ig.svelte";
    import Twitter from "./Twitter.svelte";
</script>

<div class="pt-10 pb-2 px-20 flex flex-col gap-4 bg-sky-100 text-gray-500 text-base">
    <div class=" flex flex-row justify-between items-center">
        <div class="w-fit flex flex-row gap-5">
            <a href="#" class="text-sky-400">Beranda</a>
        </div>
<!--        <div class="flex flex-row gap-4">-->
<!--            <a href="" target="_blank"><Wa/></a>-->
<!--&lt;!&ndash;            <a href="" target="_blank"><Ig/></a>&ndash;&gt;-->
<!--&lt;!&ndash;            <a href="" target="_blank"><Twitter/></a>&ndash;&gt;-->
<!--        </div>-->
    </div>

    <div class="flex flex-col justify-between gap-2">
        <div>Jl. Jendral Ahmad Yani No. 4, Wua-Wua, Kendari</div>
<!--        <div>Email info@stnk.com</div>-->
        <div class="flex flex-row"><Wa/>&nbsp;&nbsp;<span>+62 822-6625-3923</span></div>
        <div class="flex flex-row"><Wa/>&nbsp;&nbsp;<span>+62 851-5916-0805</span></div>
<!--        <div>Fax +62 85228608215</div>-->
    </div>

    <div class="flex flex-col items-center text-xs">
        <span>Copyright © 2023 Kendari</span>
    </div>
</div>

