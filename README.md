# ad-tier-stub-server

### API server

### `/streaming-demo/assets`

```ts
type Asset = {
    id: string; // UUID
    title: string; // 视频标题
    poster: string; // 视频封面 URL
    manifest: string; // 视频 URL
    duration: number; // 视频正片时长
    adUrl: string; // 包含了广告接口的 sessionId，每次播放时都会生成新的 sessionId，这里硬编码了
};

type Response = Asset[];
```

### `/streaming-demo/ads/{sessionId}`

```ts
type AdInfo = {
    adId: string;
    startTimeInSeconds: number;
    durationInSeconds: number;
};

type Avail = {
    availId: string;
    ads: AdInfo[];
    startTimeInSeconds: number;
    durationInSeconds: number;
};

type Response = {
    sessionId: string;
    avails: Avail[];
};
```
