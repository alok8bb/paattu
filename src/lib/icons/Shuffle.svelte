<script>
    import { currentPlaylist, index } from '$lib/store'

    function shuffle() {
        const elementAtPositionZero = $currentPlaylist.splice($index, 1)[0]; // Splice removes the element and returns it

        for (let i = $currentPlaylist.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [$currentPlaylist[i], $currentPlaylist[j]] = [$currentPlaylist[j], $currentPlaylist[i]];
        }

        $currentPlaylist.unshift(elementAtPositionZero);
        $index = 0;
    }
</script>

<svg on:click={shuffle} width="32" height="32" viewBox="0 0 8.4667 8.4667" xmlns="http://www.w3.org/2000/svg"><path d="m7.2535 1.037a0.5292 0.5292 0 1 0-0.74793 0.74793l0.18698 0.18698c-1.4782 0.17922-2.3779 1.0796-3.1554 1.8564l-0.03034 0.031047c-0.88975 0.88905-1.6313 1.6088-2.9776 1.6088a0.5292 0.5292 0 0 0 0 1.0584c1.807 0 2.8273-1.0203 3.6952-1.8882l0.03034-0.031047c0.74087-0.74087 1.378-1.3618 2.3475-1.5509l-0.096667 0.097373a0.5292 0.5292 0 0 0 0.74793 0.74793l1.0584-1.0584a0.5292 0.5292 0 0 0 0-0.74793zm-6.7243 0.90316c1.2482 0 2.121 0.48686 2.8273 1.0739-0.1009 0.098784-0.19757 0.19474-0.28929 0.28718l-0.05927 0.05927c-0.14465 0.14394-0.28012 0.278-0.40995 0.40219-0.57153-0.45864-1.1925-0.76416-2.0688-0.76416a0.5292 0.5292 0 0 1 0-1.0584zm6.1634 4.5546c-0.96808-0.11713-1.6878-0.54331-2.2875-1.0422 0.1009-0.098783 0.19757-0.19474 0.28929-0.28718l0.05927-0.05927c0.14465-0.14394 0.28012-0.278 0.40995-0.40219 0.42477 0.3408 0.87494 0.59693 1.4387 0.70559l-0.096666-0.096666a0.5292 0.5292 0 0 1 0.74793-0.74793l1.0584 1.0584a0.5292 0.5292 0 0 1 0 0.74793l-1.0584 1.0584a0.5292 0.5292 0 1 1-0.74793-0.74793z" fill="currentColor" stroke-width=".70559"/></svg>

