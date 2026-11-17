<script lang="ts">
    import { enhance } from '$app/forms';
    import { projects, profile } from '$lib/data';
    import ProjectRow from '$lib/components/ProjectRow.svelte';

    type Theme = 'light' | 'dark';
    type Status = 'idle' | 'loading' | 'success' | 'error';

    let theme: Theme = $state('light');
    let status: Status = $state('idle');
</script>

<div class="min-h-dvh bg-bg text-ink {theme === 'dark' ? 'dark' : ''} selection:bg-pink-300 selection:text-black transition-colors duration-300">
    <!-- nav -->
    <header class="border-b border-line backdrop-blur-md sticky top-0 z-50 bg-bg/80">
        <div
            class="mx-auto flex h-[60px] max-w-[1440px] items-center justify-between px-6 lg:h-[72px] lg:px-24"
        >
            <a href="/" class="text-[15px] font-semibold lg:text-base flex items-center gap-2 group">
                <span class="inline-block w-2.5 h-2.5 rounded-full bg-pink-500 animate-pulse group-hover:scale-125 transition-transform"></span>
                Valleria<span class="text-pink-500">Yuvirda</span>
            </a>

            <div class="flex items-center gap-2 lg:gap-8">
                <nav class="hidden items-center gap-7 lg:flex">
                    <a href="#proyek" class="text-sm text-muted hover:text-pink-500 transition-colors">Proyek</a>
                    <a href="#tentang" class="text-sm text-muted hover:text-pink-500 transition-colors">Tentang</a>
                    <a href="#kontak" class="text-sm text-muted hover:text-pink-500 transition-colors">Kontak</a>
                </nav>

                <button
                    type="button"
                    aria-label="Ganti tema"
                    onclick={() => (theme = theme === 'dark' ? 'light' : 'dark')}
                    class="flex h-11 w-11 items-center justify-center border border-line hover:border-pink-400 hover:bg-pink-50/10 transition-all rounded-lg"
                >
                    <svg
                        width="17"
                        height="17"
                        viewBox="0 0 24 24"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="1.5"
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        class="dark:hidden text-pink-600"
                    >
                        <path d="M21 12.8A9 9 0 1 1 11.2 3a7 7 0 0 0 9.8 9.8Z" />
                    </svg>
                    <svg
                        width="17"
                        height="17"
                        viewBox="0 0 24 24"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="1.5"
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        class="hidden dark:block text-pink-400"
                    >
                        <circle cx="12" cy="12" r="4" />
                        <path
                            d="M12 2v2M12 20v2M4.9 4.9l1.4 1.4M17.7 17.7l1.4 1.4M2 12h2M20 12h2M4.9 19.1l1.4-1.4M17.7 6.3l1.4-1.4"
                        />
                    </svg>
                </button>

                <button
                    type="button"
                    aria-label="Buka menu"
                    class="flex h-11 w-11 items-center justify-center border border-line lg:hidden rounded-lg hover:border-pink-400"
                >
                    <svg
                        width="18"
                        height="18"
                        viewBox="0 0 24 24"
                        fill="none"
                        stroke="currentColor"
                        stroke-width="1.5"
                        stroke-linecap="round"
                    >
                        <path d="M4 7h16M4 12h16M4 17h16" />
                    </svg>
                </button>
            </div>
        </div>
    </header>

    <!-- hero -->
    <section class="mx-auto max-w-[1440px] px-6 pt-16 pb-14 lg:px-24 lg:pt-[120px] relative overflow-hidden">
        <!-- Floating cute pink glow element -->
        <div class="absolute -top-10 right-10 w-72 h-72 bg-pink-400/10 rounded-full blur-3xl pointer-events-none"></div>

        <h1
            class="text-[62px] leading-[0.88] font-medium tracking-[-1.6px] lg:text-[232px] lg:tracking-[-9px]"
        >
            Valleria <span class="text-pink-500 font-serif italic text-[50px] lg:text-[180px]">C.</span> Yuvirda
        </h1>

        <div class="mt-7 flex flex-col gap-6">
            <p class="max-w-[560px] text-[17px] leading-[1.6] text-muted lg:text-xl">
                Siswa SMK jurusan PPLG. Membangun antarmuka web yang cepat, rapi, dan mudah dipakai dengan sentuhan penuh cinta.
            </p>

            <div class="flex items-center gap-3">
                <a
                    href="#proyek"
                    class="flex h-12 items-center bg-primary hover:bg-pink-600 px-6 text-[15px] font-medium text-on-primary transition-all shadow-sm hover:shadow-pink-500/20 hover:shadow-lg"
                >
                    Lihat proyek 
                </a>
                <a
                    href="#kontak"
                    class="flex h-12 items-center border border-line px-6 text-[15px] text-ink hover:border-pink-400 hover:text-pink-500 transition-colors"
                >
                    Hubungi saya
                </a>
            </div>

            <p class="font-mono text-[11px] tracking-[1.1px] text-muted flex items-center gap-2">
                <span class="inline-block w-2 h-2 rounded-full bg-pink-500 animate-ping"></span>
                TERSEDIA UNTUK PROYEK BARU — 2026
            </p>
        </div>
    </section>

    <!-- band -->
    <div class="border-t border-line relative group">
        <img
            src={theme === 'dark' ? '/images/band-dark.png' : '/images/band-light.png'}
            alt=""
            class="h-[220px] w-full object-cover lg:h-[420px] group-hover:scale-[1.01] transition-transform duration-700"
        />
        <div class="mx-auto max-w-[1440px] px-6 py-4 lg:px-24 flex justify-between items-center">
            <p class="font-mono text-[11px] tracking-[1.1px] text-muted">LAB PPLG — SMK NEGERI 8 · 2026</p>
            <span class="font-mono text-[11px] text-pink-500">✨ Code & Creativity</span>
        </div>
    </div>

    <!-- proyek -->
    <section id="proyek" class="border-t border-line">
        <div class="mx-auto max-w-[1440px] px-6 pt-5 pb-14 lg:px-24 lg:pb-24">
            <p class="font-mono text-[11px] tracking-[1.1px] text-pink-500 flex items-center gap-1.5">
                <span>📂</span> PROYEK PILIHAN
            </p>

            <div class="mt-7 flex flex-col divide-y divide-line lg:mt-10">
                {#each projects as project, i (project.title)}
                    <ProjectRow {project} index={i} />
                {/each}
            </div>
        </div>
    </section>

    <!-- tentang -->
    <section id="tentang" class="border-t border-line bg-pink-50/5 dark:bg-pink-950/5">
        <div class="mx-auto max-w-[1440px] px-6 pt-5 pb-14 lg:px-24 lg:pb-24">
            <p class="font-mono text-[11px] tracking-[1.1px] text-pink-500 flex items-center gap-1.5">
                <span>🌷</span> TENTANG SAYA
            </p>

            <div class="mt-7 flex flex-col items-start gap-8 lg:mt-10 lg:flex-row lg:gap-24">
                <div class="relative group w-full lg:w-[420px]">
                    <div class="absolute -inset-1 bg-gradient-to-r from-pink-500 to-rose-300 rounded-lg blur opacity-25 group-hover:opacity-50 transition duration-1000"></div>
                    <img
                        src={theme === 'dark' ? '/images/portrait-dark.png' : '/images/portrait-light.png'}
                        alt="Foto profil"
                        class="relative h-[428px] w-full object-cover lg:h-[525px] lg:w-[420px] rounded-lg border border-line"
                    />
                </div>

                <div class="flex w-full flex-col gap-7">
                    <p class="max-w-[520px] text-[17px] leading-[1.6] text-muted lg:text-xl">
                        {profile.bio}
                    </p>

                    <div class="flex flex-col divide-y divide-line">
                        {#each profile.facts as fact}
                            <div class="flex items-center justify-between gap-8 py-4 hover:px-2 transition-all rounded">
                                <span class="font-mono text-[11px] tracking-[1.1px] text-muted">
                                    {fact.label}
                                </span>
                                <span class="text-[15px] font-medium">{fact.value}</span>
                            </div>
                        {/each}
                    </div>

                    <div class="flex flex-col gap-3">
                        <span class="font-mono text-[11px] tracking-[1.1px] text-pink-500">KEAHLIAN UTAMA</span>
                        <div class="flex flex-wrap gap-2">
                            {#each profile.skills as skill}
                                <span
                                    class="border border-line hover:border-pink-400 hover:bg-pink-500/10 transition-colors px-3 py-[7px] font-mono text-[11px] tracking-[1.1px] text-muted rounded-full"
                                >
                                    ✨ {skill}
                                </span>
                            {/each}
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- kontak -->
    <section id="kontak" class="border-t border-line">
        <div class="mx-auto max-w-[1440px] px-6 pt-5 pb-14 lg:px-24 lg:pb-24">
            <p class="font-mono text-[11px] tracking-[1.1px] text-pink-500 flex items-center gap-1.5">
                <span>💌</span> KONTAK
            </p>

            <div class="mt-7 flex flex-col gap-8 lg:mt-10 lg:flex-row lg:gap-24">
                <p class="max-w-[420px] text-[17px] leading-[1.6] text-muted lg:text-xl">
                    Punya pertanyaan atau ingin berkolaborasi membuat sesuatu yang manis dan fungsional? Kirim pesan sekarang! 🌸
                </p>

                <form
                    method="POST"
                    action="?/kirim"
                    use:enhance={() => {
                        status = 'loading';
                        return async ({ result, update }) => {
                            await update({ reset: result.type === 'success' });
                            status = result.type === 'success' ? 'success' : 'error';
                        };
                    }}
                    class="flex w-full flex-col gap-4 lg:w-[440px] lg:shrink-0"
                >
                    <label class="flex flex-col gap-2">
                        <span class="font-mono text-[11px] tracking-[1.1px] text-muted">NAMA</span>
                        <input
                            name="nama"
                            required
                            autocomplete="name"
                            placeholder="Nama lengkap kamu"
                            class="h-12 w-full border border-line bg-bg px-3.5 text-[15px] outline-none placeholder:text-muted focus:border-pink-500 focus:ring-1 focus:ring-pink-500 rounded-md transition-all"
                        />
                    </label>

                    <label class="flex flex-col gap-2">
                        <span class="font-mono text-[11px] tracking-[1.1px] text-muted">EMAIL</span>
                        <input
                            name="email"
                            type="email"
                            required
                            autocomplete="email"
                            placeholder="nama@email.com"
                            class="h-12 w-full border border-line bg-bg px-3.5 text-[15px] outline-none placeholder:text-muted focus:border-pink-500 focus:ring-1 focus:ring-pink-500 rounded-md transition-all"
                        />
                    </label>

                    <label class="flex flex-col gap-2">
                        <span class="font-mono text-[11px] tracking-[1.1px] text-muted">PESAN</span>
                        <textarea
                            name="pesan"
                            required
                            rows="5"
                            placeholder="Tulis pesan kamu di sini..."
                            class="min-h-[120px] w-full border border-line bg-bg px-3.5 py-3 text-[15px] outline-none placeholder:text-muted focus:border-pink-500 focus:ring-1 focus:ring-pink-500 rounded-md transition-all"
                        ></textarea>
                    </label>

                    <button
                        type="submit"
                        disabled={status === 'loading'}
                        class="flex h-12 items-center justify-center gap-2 border px-6 text-[15px] font-medium rounded-md transition-all {status ===
                        'loading'
                            ? 'border-line bg-surface text-muted cursor-not-allowed'
                            : 'border-transparent bg-pink-500 hover:bg-pink-600 text-white shadow-md hover:shadow-pink-500/30'}"
                    >
                        {#if status === 'loading'}
                            <svg
                                width="16"
                                height="16"
                                viewBox="0 0 24 24"
                                fill="none"
                                stroke="currentColor"
                                stroke-width="1.5"
                                stroke-linecap="round"
                                stroke-linejoin="round"
                                class="animate-spin"
                            >
                                <path d="M12 3a9 9 0 1 0 9 9" />
                            </svg>
                            Mengirim...
                        {:else}
                            Kirim pesan ✨
                        {/if}
                    </button>

                    {#if status !== 'idle'}
                        <div class="flex items-center gap-3 border border-line px-4 py-3.5 rounded-md bg-pink-50/10">
                            {#if status === 'loading'}
                                <svg
                                    width="16"
                                    height="16"
                                    viewBox="0 0 24 24"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="1.5"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    class="animate-spin text-pink-500"
                                >
                                    <path d="M12 3a9 9 0 1 0 9 9" />
                                </svg>
                                <span class="text-sm text-muted">Mengirim pesan...</span>
                            {:else if status === 'success'}
                                <svg
                                    width="16"
                                    height="16"
                                    viewBox="0 0 24 24"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="1.5"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    class="text-pink-500"
                                >
                                    <path d="M20 6 9 17l-5-5" />
                                </svg>
                                <span class="text-sm text-pink-600 font-medium">Pesan terkirim dengan manis! Terima kasih! 💖</span>
                            {:else}
                                <svg
                                    width="16"
                                    height="16"
                                    viewBox="0 0 24 24"
                                    fill="none"
                                    stroke="currentColor"
                                    stroke-width="1.5"
                                    stroke-linecap="round"
                                    stroke-linejoin="round"
                                    class="text-danger"
                                >
                                    <circle cx="12" cy="12" r="9" />
                                    <path d="M12 8v5M12 16.5v.01" />
                                </svg>
                                <span class="text-sm text-danger">Gagal mengirim. Coba lagi ya!</span>
                            {/if}
                        </div>
                    {/if}
                </form>
            </div>
        </div>
    </section>

    <!-- footer -->
    <footer class="border-t border-line bg-pink-950/[0.02]">
        <div class="mx-auto flex max-w-[1440px] flex-col gap-10 px-6 py-14 lg:px-24">
            <p
                class="max-w-[640px] text-[34px] leading-[1.05] font-medium tracking-[-0.6px] lg:text-[48px] lg:tracking-[-1.2px]"
            >
                Mari membangun sesuatu yang <span class="text-pink-500 font-serif italic">JOSJIS</span> bersama.
            </p>

            <div
                class="flex flex-col items-start gap-4 lg:flex-row lg:items-center lg:justify-between lg:gap-6"
            >
                <a href="mailto:kamu@email.com" class="font-mono text-xs tracking-[1.1px] text-pink-500 hover:underline">
                    virdavalleria@email.com 
                </a>
                <div class="flex items-center gap-6">
                    <a href="#proyek" class="font-mono text-[11px] tracking-[1.1px] text-muted hover:text-pink-500 transition-colors">PROYEK</a>
                    <a
                        href="https://github.com/nama-kamu"
                        class="font-mono text-[11px] tracking-[1.1px] text-muted hover:text-pink-500 transition-colors">GITHUB</a
                    >
                    <a href="mailto:kamu@email.com" class="font-mono text-[11px] tracking-[1.1px] text-muted hover:text-pink-500 transition-colors">
                        EMAIL
                    </a>
                </div>
            </div>
        </div>
    </footer>
</div>