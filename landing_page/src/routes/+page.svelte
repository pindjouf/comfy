<script>
  import { onMount } from 'svelte';
  
  let copySuccess = false;
  const installCommand = 'wget https://github.com/pindjouf/comfy/releases/download/v1.1.0/comfy && chmod +x comfy';
  
  function copyToClipboard() {
    navigator.clipboard.writeText(installCommand);
    copySuccess = true;
    setTimeout(() => copySuccess = false, 2000);
  }

  onMount(() => {
    const waves = document.querySelectorAll('.vapor-wave');
    window.addEventListener('mousemove', (e) => {
      waves.forEach((wave, index) => {
        const speed = (index + 1) * 0.02;
        const x = (window.innerWidth - e.pageX) * speed;
        const y = (window.innerHeight - e.pageY) * speed;
        wave.style.transform = `translateX(${x}px) translateY(${y}px)`;
      });
    });
  });
</script>

<div class="min-h-screen bg-stone-900 text-stone-200 font-['EB_Garamond']">
  <div class="fixed inset-0 opacity-10 pointer-events-none overflow-hidden">
    <div class="vapor-wave absolute w-full h-[300px] bg-gradient-to-r from-purple-500/30 to-pink-500/30 blur-3xl transform -rotate-12"></div>
    <div class="vapor-wave absolute w-full h-[300px] top-1/3 bg-gradient-to-r from-blue-500/30 to-teal-500/30 blur-3xl transform rotate-12"></div>
  </div>

  <div class="relative z-10">
    <header class="pt-16 pb-8 text-center">
      <pre class="text-amber-500/90 font-mono text-sm md:text-base whitespace-pre-wrap">
{`   _____                 __       
  / ____|               / _|      
 | |     ___  _ __ ___ | |_ _   _ 
 | |    / _ \\| '_ \` _ \\|  _| | | |
 | |___| (_) | | | | | | | | |_| |
  \\_____\\___/|_| |_| |_|_|  \\__, |
                             __/ |
                            |___/ `}
      </pre>
      <h1 class="mt-6 text-4xl md:text-5xl font-semibold text-amber-500/90">comfy</h1>
      <p class="mt-4 text-xl text-stone-400">Make your server feel like home.</p>
    </header>

    <main class="max-w-4xl mx-auto px-6 py-12">
      <section class="mb-16">
        <div class="bg-stone-800/50 p-6 rounded-lg border border-stone-700/50 backdrop-blur-sm">
          <h2 class="text-2xl font-semibold mb-4 text-amber-500/90">Quick Install</h2>
          <div class="bg-stone-950 p-4 rounded-md font-mono text-sm relative">
            <code class="break-all">{installCommand}</code>
            <button 
              class="absolute right-2 top-1/2 -translate-y-1/2 px-3 py-1 text-xs bg-stone-800 hover:bg-stone-700 rounded transition-colors"
              on:click={copyToClipboard}
            >
              {copySuccess ? '✓ Copied' : 'Copy'}
            </button>
          </div>
        </div>
      </section>

      <section class="mb-16 grid md:grid-cols-2 gap-8">
        <div class="bg-stone-800/50 p-6 rounded-lg border border-stone-700/50 backdrop-blur-sm">
          <h3 class="text-xl font-semibold mb-3 text-amber-500/90">🛠️ Essential Tools</h3>
          <ul class="space-y-2 text-stone-300">
            <li>• Neovim (btw)</li>
            <li>• btop system monitor</li>
            <li>• Yazi file manager</li>
            <li>• And more developer essentials</li>
          </ul>
        </div>

        <div class="bg-stone-800/50 p-6 rounded-lg border border-stone-700/50 backdrop-blur-sm">
          <h3 class="text-xl font-semibold mb-3 text-amber-500/90">⚡ Smart Defaults</h3>
          <ul class="space-y-2 text-stone-300">
            <li>• Carefully curated configs</li>
            <li>• Sensible shell aliases</li>
            <li>• Modern CLI experience</li>
            <li>• Zero manual setup needed</li>
          </ul>
        </div>
      </section>

      <section class="mb-16">
        <div class="bg-stone-800/50 p-6 rounded-lg border border-stone-700/50 backdrop-blur-sm">
          <h2 class="text-2xl font-semibold mb-4 text-amber-500/90">Latest Release</h2>
          <div class="prose prose-invert max-w-none">
            <h3 class="text-lg font-semibold">v1.2.0</h3>
            <ul class="list-disc pl-5 text-stone-300">
              <li>Added missing shell aliases and improved permission handling</li>
              <li>Expanded package selection with tree-sitter support</li>
              <li>Enhanced Neovim installation reliability</li>
              <li>Fixed core functionality issues</li>
            </ul>
          </div>
        </div>
      </section>
    </main>

    <footer class="text-center pb-8 text-stone-500">
      <p>Licensed under <a href="http://www.wtfpl.net/">WTFPL</a></p>
      <div class="mt-4 space-x-4">
        <a href="https://github.com/pindjouf/comfy" class="hover:text-amber-500 transition-colors">GitHub</a>
        <a href="https://github.com/pindjouf/comfy/issues" class="hover:text-amber-500 transition-colors">Issues</a>
      </div>
    </footer>
  </div>
</div>

<style>
  @import url('https://fonts.googleapis.com/css2?family=EB+Garamond:wght@400;500;600&display=swap');
</style>
