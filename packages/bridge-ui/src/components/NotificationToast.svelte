<script lang="ts" context="module">
  import { toast } from '@zerodevx/svelte-toast';

  // TODO: better API to add title, icon, etc.
  //       e.g. toast.success(msg, { title: 'Success', icon: 'check' })

  // Toast component exposes the following API:

  export const errorToast = (msg: string, dismiss = false) => {
    toast.push(msg, {
      ...(dismiss ? { initial: 0, dismissable: true } : {}),
      theme: {
        '--toastBackground': 'rgb(248, 114, 114)',
        '--toastColor': '#242424',
      },
    });
  };

  export const successToast = (msg: string) => {
    toast.push(msg, {
      theme: {
        '--toastBarBackground': '#E81899',
        '--toastBackground': '#4d4d4d',
      },
    });
  };

  export const warningToast = (msg: string) => {
    toast.push(msg, {
      theme: {
        '--toastBackground': 'rgb(251, 189, 35)',
        '--toastColor': '#242424',
      },
    });
  };
</script>

<script lang="ts">
  import { SvelteToast, type SvelteToastOptions } from '@zerodevx/svelte-toast';

  // TODO: props
  const toastOptions: SvelteToastOptions = {
    dismissable: false,
    duration: 5000,
    pausable: false,
  };

  // TODO: props to control its position:
  //       top, bottom, left, right...
</script>

<div class="toast">
  <SvelteToast options={toastOptions} />
</div>

<style>
  /* TODO: Small devices. We need design!! */
  .toast {
    --toastContainerRight: 1rem;
    --toastContainerBottom: auto;
    --toastContainerTop: 5rem;
    --toastWidth: 100%;
    --toastMinHeight: 2rem;
    --toastPadding: 0 0.5rem;
    --toastBorderRadius: 0.4rem;
    --toastColor: #e3e3e3;
  }

  /* 
    TODO: decides at which breakpoint we are no longer
          in small screens. Design!!
   */
  @media (min-width: 640px) {
    .toast {
      --toastWidth: 18rem;
    }
  }
</style>
