<template>
    <div class="col" :class="colClass"
    :style="colStyle">
        <slot></slot>
    </div>
</template>
<script>
    let validator = (value)=>{
        let keys = Object.keys(value);
        let valid = true;
        keys.forEach(key => {
            if (!['span', 'offset'].includes(key)){
                valid = false
            }
        });
        return valid
    };
    export default {
        name:'guluRow',
        props:{
            span:{type:[Number,String]},
            offset:{type: [Number,String]},
            phone:{type: Object,validator,},
            ipad:{type: Object, validator,},
            narrowPc:{type: Object, validator,},
            pc:{type: Object, validator,},
            widePc:{type: Object, validator,}
        },
        data(){
            return {
                gutter:0
            }
        },
        methods:{
            createClasses(obj,str=''){
                if (!obj){return []}
                let array = [];
                if (obj.span){array.push(`col-${str}${obj.span}`)}
                if (obj.offset){array.push(`offset-${str}${obj.offset}`)}
                return array;
            }
        },
        computed:{
            colClass: function () {
                let {span, offset, phone,ipad,narrowPc,pc,widePc} = this;
                let createClasses = this.createClasses;
                return [
                    ...createClasses({span,offset}),
                    ...createClasses(phone,'phone-'),
                    ...createClasses(ipad,'ipad-'),
                    ...createClasses(narrowPc,'narrowPc-'),
                    ...createClasses(pc,'pc-'),
                    ...createClasses(widePc,'widePc-')
                ]
            },
            colStyle(){
                return {
                    paddingLeft: this.gutter/2 + 'px',
                    paddingRight: this.gutter/2 + 'px'
                }
            }
        }
    }
</script>
<style lang="scss" scoped>
    .col{
        background: grey;
        border:1px solid red;
        height: 32px;
        width: 50%;
    
        $class-prefix: col-;
        @for $n from 1 through 24 {
            &.#{$class-prefix}#{$n}{
                width: ($n / 24) * 100%;
            }
        }

        $class-prefix: offset-;
        @for $n from 1 through 24 {
            &.#{$class-prefix}#{$n}{
                margin-left: ($n / 24) * 100%;
            }
        }

        @media (max-width: 576px) {
            $class-prefix: col-phone-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    width: ($n / 24) * 100%;
                }
            }
            $class-prefix: offset-phone-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    margin-left: ($n / 24) * 100%;
                }
            }

        }
        @media (min-width: 577px) {
            $class-prefix: col-ipad-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    width: ($n / 24) * 100%;
                }
            }
            $class-prefix: offset-ipad-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    margin-left: ($n / 24) * 100%;
                }
            }

        }
        @media (min-width: 768px) {
            $class-prefix: col-narrowPc-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    width: ($n / 24) * 100%;
                }
            }
            $class-prefix: offset-narrowPc-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    margin-left: ($n / 24) * 100%;
                }
            }
        }
        @media (min-width: 992px)  {
            $class-prefix: col-pc-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    width: ($n / 24) * 100%;
                }
            }
            $class-prefix: offset-pc-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    margin-left: ($n / 24) * 100%;
                }
            }

        }
        @media (min-width: 1200px){
            $class-prefix: col-widePc-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    width: ($n / 24) * 100%;
                }
            }
            $class-prefix: offset-widePc-;
            @for $n from 1 through 24 {
                &.#{$class-prefix}#{$n}{
                    margin-left: ($n / 24) * 100%;
                }
            }

        }

    }
</style>