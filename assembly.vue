/* 	标题组件
 *	参数：
 *		prop.title
 *		prop.childActive
 *		prop.items
 */
Vue.component('wx-head',{
	props: ['prop'],
	template: '\
		<header>\
			<h1>{{prop.title}}</h1>\
			<div class="r-group">\
				<button class="btn-search" type="button">search</button>\
				<div class="drop-grop">\
					<button class="add-btn" type="button" v-on:click="changeChild">add</button>\
					<ul class="child-list" v-if="prop.childActive">\
						<li v-for="item in prop.items" :class="item.icon">{{item.text}}</li>\
					</ul>\
				</div>\
			</div>\
		</header>\
	',
	methods: {
		changeChild: function () {
			this.prop.childActive = !this.prop.childActive;
		}
	}
});

/*	列表组件
 *	prop.title
 *	prop.description
 *	prop.src
 *	prop.alt
 */
Vue.component('wx-list',{
	props: ['prop'],
	template: '\
		<section class="wx-list">\
			<dl v-for="item in prop">\
				<dt>\
					<img :src="item.src" :alt="item.alt">\
				</dt>\
				<dd>\
					<h2>{{item.title}}</h2>\
					<p>{{item.description}}</p>\
					<time>{{item.time}}</time>\
				</dd>\
			</dl>\
		</section>\
	'
});

/*	底部组件
 *	prop.icon
 *	prop.name
 */
 Vue.component('wx-foot',{
 	props: ['prop'],
 	template: '\
 		<footer class="wx-foot">\
 			<ul>\
 				<li v-for="item in prop" :class="current(item)" @click="currActive">{{item.name}}</li>\
 			</ul>\
 		</footer>\
 	',
 	methods: {
 		current: function (e) {
			var icon = '',
				iconName = e.icon.split(' ')[1];

 			if (e.active) {
 				icon =  e.icon + ' ' + iconName+'-current';
 			} else {
 				icon = e.icon;
 			}
 			return icon;
 		},
 		currActive: function () {
 			// console.log(this);

 		}
 	}
 })