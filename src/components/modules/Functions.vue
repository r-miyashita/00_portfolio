<script lang="ts">

function addIo(target: string, key: string): void {
    const els = document.querySelectorAll(target);
    const addition = key;
    const addClass = (entries: any): void => {
        entries.forEach( (entry: any) => {
            if(entry.isIntersecting && !entry.target.classList.contains(addition)) {
                entry.target.classList.add(addition);
            }
        });
    }; 
    const io = new IntersectionObserver(addClass);
    els.forEach(el => {
        io.observe(el);
    });
}

export { addIo };
</script>