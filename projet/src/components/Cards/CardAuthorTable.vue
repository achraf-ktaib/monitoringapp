<template>
	<!-- Energy Consumption Table Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{ padding: '16px' }">
	  <template #title>
		<a-row type="flex" align="middle">
		  <a-col :span="24" :md="12">
			<h5 class="font-semibold m-0">Energy Consumption Table</h5>
		  </a-col>
		  <a-col :span="24" :md="12" style="display: flex; align-items: center; justify-content: flex-end">
			<a-radio-group v-model="filterType" size="small">
			  <a-radio-button value="all">ALL</a-radio-button>
			  <a-radio-button value="high">HIGH</a-radio-button>
			  <a-radio-button value="low">LOW</a-radio-button>
			</a-radio-group>
		  </a-col>
		</a-row>
	  </template>
	  <a-table :columns="columns" :data-source="data" :pagination="false" :scroll="{ y: 240 }">
		<template slot="company" slot-scope="company">
		  <div class="table-avatar-info">
			<a-avatar shape="square" :src="company.logo" />
			<div class="avatar-info">
			  <h6>{{ company.name }}</h6>
			  <p>{{ company.industry }}</p>
			</div>
		  </div>
		</template>
  
		<template slot="consumption" slot-scope="consumption">
		  <div class="consumption-info">
			<h6 class="m-0">{{ consumption.value }} kWh</h6>
			<p class="m-0 font-regular text-muted">{{ consumption.period }}</p>
		  </div>
		</template>
  
		<template slot="status" slot-scope="status">
		  <a-tag class="tag-status" :class="status === 'High' ? 'ant-tag-primary' : 'ant-tag-muted'">
			{{ status }}
		  </a-tag>
		</template>
  
		<template slot="action" slot-scope="row">
		  <a-button type="link" :data-id="row.key" class="btn-edit">
			Details
		  </a-button>
		</template>
	  </a-table>
	</a-card>
	<!-- / Energy Consumption Table Card -->
  </template>
  
  <script>
  export default {
	props: {
	  data: {
		type: Array,
		default: () => [],
	  },
	  columns: {
		type: Array,
		default: () => [
		  {
			title: 'Company',
			dataIndex: 'company',
			scopedSlots: { customRender: 'company' },
		  },
		  {
			title: 'Consumption',
			dataIndex: 'consumption',
			scopedSlots: { customRender: 'consumption' },
		  },
		  {
			title: 'Status',
			dataIndex: 'status',
			scopedSlots: { customRender: 'status' },
		  },
		  {
			title: 'Action',
			dataIndex: 'action',
			scopedSlots: { customRender: 'action' },
		  },
		],
	  },
	},
	data() {
	  return {
		// Filter type for the energy consumption table.
		filterType: 'all',
	  };
	},
  };
  </script>
  
  <style scoped>
  .table-avatar-info {
	display: flex;
	align-items: center;
	gap: 8px;
  }
  
  .avatar-info h6 {
	margin: 0;
	font-weight: 600;
  }
  
  .avatar-info p {
	margin: 0;
	color: #888;
	font-size: 12px;
  }
  
  .consumption-info h6 {
	font-weight: 600;
  }
  
  .consumption-info p {
	font-size: 12px;
	color: #888;
  }
  
  .tag-status.ant-tag-primary {
	background-color: #ff4d4f;
	color: white;
	border: none;
  }
  
  .tag-status.ant-tag-muted {
	background-color: #d9d9d9;
	color: #888;
	border: none;
  }
  
  .btn-edit {
	color: #1890ff;
	padding: 0;
  }
  </style>
  