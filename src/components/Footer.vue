<template>
	<footer>
		<div class="footer-container">
			<div class="col first">
				<logo class="footer light" />
				<p class="copyright">
					&copy; 2022-2025 BambooPixel & Cloudery<br />
					<small>网站基于 Vue 2 · 我们❤️开源</small><br />
					<small>Latest built at {{ latestBuildDate }}</small>
				</p>
				<p>BambooPixel 致力于实现高自由度、带有探索性的游戏体验。插件的多样性承载着我们的追求。</p>
				<p>注：如无特殊说明，所有文字的著作权和游戏摄影作品使用权归 竹像素 所有。部分图片来自于公有领域。</p>
			</div>
			<div class="links">
				联系服主(柒屹) — <a href="mailto:justqiyi@qq.com">justqiyi@qq.com</a><br/>
				联系服主(云竹) — <a href="mailto:2457483710@qq.com">2457483710@qq.com</a><br/>
				团队邮箱 — <a href="mailto:admin@cldery.com">admin@cldery.com</a>
			</div>
			<div class="button-list">
				<icon-btn @click.native="$open('https://github.com/clouderystudio')" icon="github" class="dark" />
				<icon-btn @click.native="$open('https://doc.cldery.com/game/mc')" icon="book-outline" class="dark" />
			</div>
		</div>
	</footer>
</template>

<script lang="ts">
import Vue from 'vue';
import Logo from './Logo.vue';
import IconBtn from '@/components/IconBtn.vue';
import { toStandardDate } from '@/fn';

export default Vue.extend({
	components: { Logo, IconBtn },
	computed: {
		latestBuildDate() {
			return !!document.documentElement.dataset['buildTimestamp'] ? toStandardDate(document.documentElement.dataset['buildTimestamp']) : 'unknown';
		}
	}
});
</script>

<style lang="less" scoped>
footer {
	box-shadow: 0px -2px 10px rgba(0, 0, 0, 0.4);
	background: #212121;
	color: white;
	.links {
		@media (max-width: 1000px) {
			position: static;
			text-align: center;
			margin: 8px 0;
		}

		position: absolute;
		right: 0;
		bottom: calc(32px + 14px);
		text-align: right;
		color: @textmidwhite;
		font-size: 14px;
		a {
			margin-top: 5px;
			border-bottom: 1px solid rgba(255, 255, 255, 0.3);
			transition: all 0.2s ease;
			display: inline-block;
			&:hover {
				color: white;
				border-color: white;
			}
		}
	}

	.footer-container {
		display: block;
		margin: auto;
		padding: 32px 56px;
		width: 70%;
		position: relative;

		.col {
			&.first {
				p {
					color: @textmidwhite;
					font-size: 14px;
					max-width: 400px;
				}

				.copyright {
					color: white;
				}

				.light {
					margin-bottom: 32px;
				}
			}
		}
	}
}

.button-list {
	display: flex;
	> * {
		margin: 8px 5px;
	}
	@media (max-width: 1000px) {
		justify-content: center;
	}
	@media screen and (min-width: 1000px) {
		position: absolute;
		top: 32px;
		right: 0;
	}
}
</style>
