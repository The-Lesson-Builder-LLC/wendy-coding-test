<template>
    <dl class="space-y-4 mx-6 my-6">
      <Disclosure as="div" v-for="(domain, index) in domains" :key="index" v-slot="{ open }">
        <dt>
          <DisclosureButton class="flex w-full text-left text-gray-900">
            <span class="mr-6 flex h-7 items-center">
              <PlusSmallIcon v-if="!open" class="h-6 w-6" aria-hidden="true" />
              <MinusSmallIcon v-else class="h-6 w-6" aria-hidden="true" />
            </span>
            <span class="text-base font-semibold leading-7">{{ domain.name }}</span>
          </DisclosureButton>
        </dt>
            <transition
            enter-active-class="transition duration-500 ease-out"
            enter-from-class="transform scale-95 opacity-0"
            enter-to-class="transform scale-100 opacity-100"
            leave-active-class="transition duration-75 ease-out"
            leave-from-class="transform scale-100 opacity-100"
            leave-to-class="transform scale-95 opacity-0"
            >
                <DisclosurePanel as="dd" class="pr-12">
                    <sub-domains :subDomains="domain.sub_domains" />
                </DisclosurePanel>
            </transition>
      </Disclosure>
    </dl>
</template>

<script>
    import { Disclosure, DisclosureButton, DisclosurePanel } from '@headlessui/vue'
    import { MinusSmallIcon, PlusSmallIcon } from '@heroicons/vue/24/outline'
    import SubDomains from './SubDomains.vue';

    export default {
        components: {
            Disclosure,
            DisclosureButton,
            DisclosurePanel,
            MinusSmallIcon,
            PlusSmallIcon,
            SubDomains
        },
        props: ['domains'],
        data() {
            return {}
        }
    }
</script>
