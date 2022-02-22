<page>
    <actionBar title="Xronos" />

    <tabView>
        <tabViewItem title="Timers">
            <gridLayout columns="*,120" rows="70,*">
                <textField col="0" row="0" bind:text={textFieldValue} hint="Type a timer time..." editable="true" on:returnPress="{onButtonTap}" />
                <button col="1" row="0" text="Add Timer" on:tap="{onButtonTap}" />

                <listView items="{timers}" on:itemTap="{onItemTap}" row="1" colSpan="2">
                    <!-- <Template let:item>
                        <label text="{item.name}" textWrap="true" />
                    </Template> -->
                </listView>
            </gridLayout>
        </tabViewItem>
        <tabViewItem title="Clocks">
            <label textWrap="true">This tab shows the user's clocks.</label>
        </tabViewItem>
    </tabView>
</page>

<script lang="ts">
    // import {Template} from 'svelte-native/components'

    let timers: any[] = []
    let textFieldValue: string = ""

    function onItemTap(args:any) {
        console.log(`Item ${timers[args.index].name} at index: ${args.index} was tapped`);
    }

    function onButtonTap() {
        if (textFieldValue === "") return;
        console.log(`New timer added: ${textFieldValue}.`);
        timers = [{name : textFieldValue}, ...timers];
        textFieldValue = "";
    }
</script>

<style>
    .info .fas {
        color: #3A53FF;
    }

    .info {
        font-size: 20;
        horizontal-align: center;
        vertical-align: center;
    }
</style>
