# ad-tier-stub-server

- 可以通过 GitHub Pages 直接访问，各个资源的访问地址在下面详情里
- 也可以 clone 这个 repo 到本地 host 起来

## API server

### `https://changancity.github.io/ad-tier-stub-server/api/playlist`

```ts
type Response = {
    id: string; // UUID
    title: string; // 视频标题
    poster: string; // 视频封面 URL
    manifest: string; // 视频 URL
    duration: number; // 视频正片时长
    adUrl: string | null; // 包含了广告接口的 sessionId，每次播放时都会生成新的 sessionId，这里硬编码了
}[];
```

### `https://changancity.github.io/ad-tier-stub-server/api/ads/{sessionId}`

Sample: https://changancity.github.io/ad-tier-stub-server/api/ads/02

```ts
type Response = {
    sessionId: string;
    avails: {
        availId: string;
        ads: {
            adId: string;
            startTimeInSeconds: number;
            durationInSeconds: number;
        }[];
        startTimeInSeconds: number;
        durationInSeconds: number;
    }[];
};
```

## Resources server

主要提供了一些 DASH manifests，可以直接用 DASH Industry Forum 的 [Reference player](http://reference.dashif.org/dash.js/nightly/samples/dash-if-reference-player/index.html) 播放

- https://changancity.github.io/ad-tier-stub-server/resources/dash/ad-free.mpd
- https://changancity.github.io/ad-tier-stub-server/resources/dash/pre-roll-1-ad-mid-roll-1-ad.mpd
- https://changancity.github.io/ad-tier-stub-server/resources/dash/pre-roll-2-ads.mpd
- https://changancity.github.io/ad-tier-stub-server/resources/dash/mid-roll-2-ads.mpd
