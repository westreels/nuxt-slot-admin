<template>
    <v-container>
        <v-row>
            <v-col class="mt-0">
                <MM_Multiple_Options  
                    :value = 'data.type_game'
                    :action = 'action' 
                    :title = '"Type game"' 
                    :action_key = '"type_game"'/>
                <MM_Input
                    :value = 'data.rtp'
                    :action = 'action' 
                    :title = '"Rtp"' 
                    :action_key = '"rtp"'
                />
                 <MM_Rating 
                    :value = 'data.rating'
                    :action = 'action' 
                    :title = '"Rating"' 
                    :action_key = '"rating"'
                />
                <MM_Input
                    :value = 'data.min_bet'
                    :action = 'action' 
                    :title = '"Min bet"' 
                    :action_key = '"min_bet"'
                />
                <MM_Input
                    :value = 'data.max_bet'
                    :action = 'action' 
                    :title = '"Max bet"' 
                    :action_key = '"max_bet"'
                />
                <MM_Input
                    :value = 'data.number_rows'
                    :action = 'action' 
                    :title = '"Number rows"' 
                    :action_key = '"number_rows"'
                />
                <MM_Input
                    :value = 'data.pay_lines'
                    :action = 'action' 
                    :title = '"Pay Lines"' 
                    :action_key = '"pay_lines"'
                />
                <MM_Input
                    :value = 'data.reels'
                    :action = 'action' 
                    :title = '"Reels"' 
                    :action_key = '"reels"'
                />
                <MM_Options  
                    :value = 'data.volatility' 
                    :all_value = '["high", "medium", "low"]'
                    :title = '"Volatility"'
                    :action = 'action'
                    :action_key = '"volatility"'
                                 />
                <MM_Checkbox 
                    :value = 'data.bonus_rounds'
                    :action = 'action' 
                    :title = '"Bonus rounds"' 
                    :action_key = '"bonus_rounds"'
                />
                <MM_Checkbox 
                    :value = 'data.free_spins'
                    :action = 'action' 
                    :title = '"Free spins"' 
                    :action_key = '"free_spins"'
                />
                <MM_Checkbox 
                    :value = 'data.scatters'
                    :action = 'action' 
                    :title = '"Scatters"' 
                    :action_key = '"scatters"'
                />
                <MM_Checkbox 
                    :value = 'data.wild_symbol'
                    :action = 'action' 
                    :title = '"Wild symbol"' 
                    :action_key = '"wild_symbol"'
                />
                <MM_Image 
                    :value = 'data.icon' 
                    :title = '"Icon"'
                    :action = 'action'
                    :action_key = '"icon"' 
                />
                <MM_Multiple_Input
                    :value = 'data.ref'
                    :action = 'action' 
                    :title = '"Referal link"' 
                    :action_key = '"ref"'
                />
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
    import MM_Multiple_Input_Text from '../../lib/MM_Multiple_Input_Text'
    import MM_Input from '../../lib/MM_Input'
    import MM_Multiple_Input from '../../lib/MM_Multiple_Input'
    import MM_Checkbox from '../../lib/MM_Checkbox'
    import MM_Multiple_Options from '../../lib/MM_Multiple_Options'
    export default {
        name: "slotMeta",
        props: ['data', 'action'],
        components: {MM_Multiple_Input_Text, MM_Input, MM_Multiple_Input, MM_Checkbox},
        data() {
            return {}
        },
        mounted(){
            console.log(this.data)
        }
    }
</script>