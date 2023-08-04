<script>
	import Button from '../components/Button.svelte';
	const features = [
		{
			title: 'Upload & Organize',
			icon: 'upload',
			description:
				'Upload in bulk, organize content in categories, add custom filters & upload extras.'
		},
		{
			title: 'Stream On-Demand',
			icon: 'record',
			description: 'Showcase your content in a beautiful on-demand video catalog.'
		},
		{
			title: 'Stream live',
			icon: 'stream',
			description: 'Schedule events in advance & build excitement with a countdown overlay.'
		},
		{
			title: 'Monetization',
			icon: 'monetization',
			description: 'Offer subscriptions or one-time purchases. Accept credit cards & PayPal.'
		},
		{
			title: 'Analytics',
			icon: 'stream',
			description: 'Know what your audience likes & how your content is performing.'
		},
		{
			title: 'For all devices',
			icon: 'device',
			description: 'Get organized on all devices'
		}
	];
</script>

<section class="py-20 text-white bg-black">
	<div class="max-w-screen-xl mx-auto">
		<div class="flex items-center space-x-24">
			<div class="flex flex-col w-1/2">
				<div class="flex flex-col space-y-4">
					<h1 class="text-5xl font-bold font-heading">제목</h1>
					<p>
						You know, without you, I'm so lonely. When you're not here, 911 calling. Into your heat
						again, I'm diving. Darling you, darling you, baby
					</p>
				</div>
				<div class="flex mt-12 space-x-3">
					<div class="w-1/3">
						<Button primary={true}>시작하자</Button>
					</div>
					<div class="w-1/3">
						<Button second={true}>로그인</Button>
					</div>
				</div>
				
			</div>
			<div class="relative w-1/2">
				<img src="/images/hero-image-desktop.png" alt="Image1" class="w-full h-full" />
				<img
					src="/images/hero-image-mobile.png"
					alt="Image2"
					class="absolute -bottom-4 -left-3"
				/>
			</div>
		</div>
		<div class="flex justify-between mt-32 space-x-24">
			<img
				src="/images/apple-tv.svg"
				class="transform transition duration-300 hover:scale-110 cursor-pointer"
				alt="Apple TV"
			/>
			<img
				src="/images/android-tv.svg"
				class="transform transition duration-300 hover:scale-110 cursor-pointer"
				alt="Android TV"
			/>
			<img
				src="/images/apple-watch.svg"
				class="transform transition duration-300 hover:scale-110 cursor-pointer"
				alt="Apple Watch"
			/>
			<img
				src="/images/iphone.svg"
				class="transform transition duration-300 hover:scale-110 cursor-pointer"
				alt="iPhone"
			/>
			<img
				src="/images/android.svg"
				class="transform transition duration-300 hover:scale-110 cursor-pointer"
				alt="Android"
			/>
		</div>
	</div>
</section>

<section class="py-20 bg-gray-400">
	<div class="max-w-screen-lg mx-auto">
		<div class="flex flex-col justify-center text-center">
			<div class="flex flex-col space-y-3">
				<h2 class="text-4xl font-bold font-heading">Rock With You</h2>
				<p>This time, I want to rock with you. Moon light, is shining like as you.</p>
			</div>
			<div class="flex justify-center mt-12 space-x-8">
				<div class="w-1/6">
					<Button primary={true}>시작하자</Button>
				</div>
				<div class="w-1/6">
					<Button second={true}>로그인</Button>
				</div>
			</div>
		</div>
		<div class="grid grid-cols-3 gap-8 mt-20">
			{#each features as feature}
				<div
					class="flex flex-col p-4 space-y-3 hover:shadow-xl transition duration-300 cursor-pointer"
				>
					<div class="flex space-x-3">
						<img
							src={`/icons/${feature.icon}.svg`}
							class="transform transition duration-300 hover:rotate-12"
							alt={feature.title}
						/>
						<h5 class="font-bold font-heading">{feature.title}</h5>
					</div>
					<p>{feature.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<section class="py-20 text-white bg-black">
	<div class="flex flex-col max-w-screen-xl mx-auto space-y-32">
		<div class="flex flex-col justify-center">
			<h2 class="text-4xl font-bold text-center font-heading">제목제목</h2>
		</div>
		<div class="flex space-x-4">
			<div class="flex flex-col justify-center w-1/2 space-y-6">
				<h5 class="text-3xl font-semibold">소제목제목제목</h5>
				<p>
					내용내용
				</p>
				<div class="flex space-x-3 cursor-pointer group">
					<p class="transition font-heading group-hover:font-bold">
						START
					</p>
					<img src="/icons/arrow.svg" class="transition transform group-hover:translate-x-1" alt="Arrow Icon">
				</div>
			</div>
			<div class="relative w-1/2">
				<img src="/images/monetization.png"  class="w-full h-full" alt="Monetize">
				<div>

				</div>
			</div>
		</div>
	</div>

	<div class="flex space-x-24">
		<div class="relative flex w-1/2">
			<img src="/images/optimized.png" class="w-full h-full" alt="Optimized">
			<div class="absolute px-4 py-3 bg-white -top-4 -right-4 rounded-2xl">
				<div class="relative">
					<img src="/icons/email-black.svg" class="w-8 h-6" alt="Email Icon">
					<span class="absolute text-xs rounded-full -top-2 -right-2 bg-blue-300 px-[6px] py-[1px] font-heading font-bold">1</span>
				</div>
			</div>
		</div>
		<div class="flex flex-col justify-center w-1/2 space-y-6">
			<h5 class="text-3xl font-semibold">중제목</h5>
			<p>내용내용좋은내용</p>
			<div class="flex space-x-3 cursor-pointer group">
				<p class="transition font-heading group-hover:translate-x-1">시작시작</p>
				<img src="/icons/arrow.svg" class="transition transfrom group-hover:translate-x-1"  alt="Arrow Icon">
			</div>
		</div>
	</div>
</section>

<section class="pt-20 pb-40 text-white bg-pink-600">
	<div class="flex flex-col max-w-screen-lg mx-auto">
		<div class="flex flex-col space-y-3 text-center">
			<h2 class="text-4xl font-bold font-heading">핑크제목</h2>
			<p>역시 핫핑크 최고다</p>
		</div>
		<div class="flex justify-center space-x-8 mt-14">
			<div class="w-1/5"><Button primary={true}/></div>
			<div class="w-1/5"><Button second={true}/></div>
		</div>
		<div class="relative mt-20">
			<img src="/images/business-desktop.png" class="w-full h-full" alt="BDT">
			<img src="/images/business-mobile.png"  class="absolute -bottom-12 -left-3" alt="BDTM">
		</div>
	</div>
</section>

<section class="pt-20 pb-32">
	<div class="flex flex-col justify-center space-y-3 text-center">
		<h2 class="text-4xl font-bold font-heading">Famous live on our platform</h2>
		<p>At the end of the day have fun with celebrities</p>
	</div>

	<div class="flex flex-col overflow-hidden mt-24 space-y-6">
		<div class="flex space-x-8">
			<img src="/images/showcase-1.png" alt="Showcase 1" class="w-[360px] h-[201px]" />
			<img src="/images/showcase-2.png" alt="Showcase 2" class="w-[360px] h-[201px]" />
			<img src="/images/showcase-3.png" alt="Showcase 3" class="w-[360px] h-[201px]" />
			<img src="/images/showcase-4.png" alt="Showcase 4" class="w-[360px] h-[201px]" />
		</div>
		<div class="flex space-x-8 -translate-x-72">
			<img src="/images/showcase-5.png" alt="Showcase 5" class="w-[360px] h-[201px]" />
			<img src="/images/showcase-6.png" alt="Showcase 6" class="w-[360px] h-[201px]" />
			<img src="/images/showcase-7.png" alt="Showcase 7" class="w-[360px] h-[201px]" />
			<img src="/images/showcase-8.png" alt="Showcase 8" class="w-[360px] h-[201px]" />
			<img src="/images/showcase-9.png" alt="Showcase 9" class="w-[360px] h-[201px]" />
		</div>
	</div>
</section>