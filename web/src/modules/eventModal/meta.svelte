<script lang="ts">
  import Buildings from '../icons/buildings.svelte'
  import Time from '../icons/time.svelte'

  import type { GoogleCalendarItem } from '$types/GoogleCalendar'
  import TimeStringify from '../event/timeStringify.svelte'

  // prettier-ignore
  export let item: GoogleCalendarItem;
</script>

<section>
  <h3 class="text-lg font-medium leading-6 text-gray-900 dark:text-white">
    {item.summary}
  </h3>
  {#if item.location}
    <div class="flex pt-2 items-center space-x-1 text-sm">
      <Buildings class="w-4 h-4 shrink-0" />
      <a
        target="_blank"
        rel="noreferrer"
        href={`https://www.google.com/maps/search/${item.location}`}
        >{item.location}</a
      >
    </div>
  {/if}
  <div class="flex pt-2 items-center space-x-1 text-sm">
    <Time class="w-4 h-4 shrink-0" />
    <TimeStringify calendarTime={item.start} />
    <span>-</span>
    <TimeStringify calendarTime={item.end} />
  </div>
</section>

<div class="w-full border-b my-3" />
