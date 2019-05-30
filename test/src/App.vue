<template>
    <div class="example-wrap">
        <div class="block">
            <el-multi-cascader class="multi-cascader"
                :options="options"
                multiple
                :currentActiveValue="currentActiveValue ? [1, 11, 51] : []"
                :select-children="selectChildren"
                :only-out-put-leaf-node="onlyOutPutLeafNode"
                :collapse-tags="collapseTags"
                :filterable="filterable"
                :show-all-levels="showAllLevels"
                :expand-trigger="expandTrigger"
                :separator="separator"
                :disabled="disabled"
                @change="valueChange"
                :clearable="clearable"
                :change-on-select="changeOnSelect"
                :append-to-body="appendToBody"
                @active-item-change="handleItemChange"
                size="medium"
                parent-el=".multi-cascader"
                v-model="selectedOptions">
            </el-multi-cascader>
        </div>
    </div>
</template>


<script>
export default {
  name: 'HelloWorld',
    data() {
        const optionsShow = [{
            label: "默认",
            id: -1,
            children: [],
            value: -1
        },
        {
            label: "电信",
            children: [{
                label: "华东电信",
                children: [{
                    label: "安徽电信",
                    id: 51,
                    children: null,
                    value: 51
                },
                {
                    label: "福建电信",
                    id: 52,
                    children: null,
                    value: 52
                },
                {
                    label: "江苏电信",
                    id: 53,
                    children: null,
                    value: 53
                }],
                id: 11,
                value: 11
            },
            {
                label: "华南电信",
                children: [{
                    label: "广东电信",
                    id: 58,
                    children: null,
                    value: 58
                },
                {
                    label: "广西电信",
                    id: 59,
                    children: null,
                    value: 59
                }],
                id: 12,
                value: 12
            }],
            id: 1,
            value: 1
        },
        {
            label: "联通",
            children: [{
                label: "华东联通",
                children: [{
                    label: "安徽联通",
                    id: 91,
                    children: null,
                    value: 91
                },
                {
                    label: "福建联通",
                    id: 92,
                    children: null,
                    value: 92
                },
                {
                    label: "江苏联通",
                    id: 93,
                    children: null,
                    value: 93
                }],
                id: 21,
                value: 21,
                disabled: false
            },
            {
                label: "华南联通",
                children: [{
                    label: "广东联通",
                    id: 98,
                    children: null,
                    value: 98
                },
                {
                    label: "广西联通",
                    id: 99,
                    children: null,
                    value: 99
                },
                {
                    label: "海南联通",
                    id: 100,
                    children: null,
                    value: 100
                }],
                id: 22,
                value: 22,
                disabled: true
            }],
            id: 2,
            value: 2,
            disabled: true
        },
        {
            label: "移动",
            children: [{
                label: "华东移动",
                children: [{
                    label: "安徽移动",
                    id: 131,
                    children: null,
                    value: 131
                }],
                id: 31,
                value: 31,
                disabled: true
            },
            {
                label: "华南移动",
                children: [{
                    label: "广东移动",
                    id: 138,
                    children: null,
                    value: 138
                },
                {
                    label: "广西移动",
                    id: 139,
                    children: null,
                    value: 139
                },
                {
                    label: "海南移动",
                    id: 140,
                    children: null,
                    value: 140
                }],
                id: 32,
                value: 32,
                disabled: true
            }],
            id: 3,
            value: 3,
            disabled: false
        }];
        return {
            selectedOptions: [[1, 11, 51 ]],
            optionsShow: JSON.parse(JSON.stringify(optionsShow)),
            options: JSON.parse(JSON.stringify(optionsShow)),
            appendToBody: true,
            multiple: true,
            selectChildren: false,
            onlyOutPutLeafNode: false,
            collapseTags: false,
            filterable: true,
            showAllLevels: true,
            expandTrigger: 'click',
            separator: '-',
            disabled: false,
            clearable: true,
            changeOnSelect: true,
            currentActiveValue: false
        }
    },
    methods: {
        valueChange($event) {
            // console.log($event);
        },
        handleItemChange($event) {
            if ($event[0] === -1) {
                setTimeout(() => {
                    this.options[0].children = [{
                        label: "异步加载的二级",
                        children: [{
                            label: "安徽电信",
                            id: 51,
                            children: null,
                            value: 51
                        },
                        {
                            label: "福建电信",
                            id: 52,
                            children: null,
                            value: 52
                        },
                        {
                            label: "江苏电信",
                            id: 53,
                            children: null,
                            value: 53
                        }],
                        id: 11,
                        value: 11
                    }]
                }, 1000);

            }
        }
    },
};
</script>
<style lang="less">
.example-wrap {
    height: 100%;
}
.block {
    display: inline-block;
    vertical-align: top;
    margin: 20px 5px;
    width: calc(100vw - 540px);

    .multi-cascader {
        margin-bottom: 10px;
        width: 300px;
    }
}
</style>
