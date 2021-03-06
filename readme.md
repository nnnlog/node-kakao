# NodeKakao - Loco protocol compatible library

Note: this implemention can stop working anytime.

## Version Information

| v3 | (Recommended) Current |
|----|-----------------------|
| v2 |      deprecated       |
| v1 | experimental. buggy   |

## Warning

Many functions that I may not know are disabled or tricked to keep this client simple.

## Example code

```javascript
let client = new TalkClient('TEST_CLIENT-UWP');

client.on('message', (chat: Chat) => {
    let userInfo = chat.Channel.getUserInfo(chat.Sender);

    if (!userInfo) return;

    if (chat.Type === ChatType.Search) {
        let attachment = chat.AttachmentList[0] as SharpAttachment;

        chat.replyText(`${userInfo.Nickname}님이 샵 검색 전송 ${attachment.Question}. 리다이렉트 경로: ${attachment.RedirectURL}`);
    }

    if (chat.Text === '안녕하세요') {
        chat.replyText('안녕하세요 ', new ChatMention(userInfo)); // Ex) 안녕하세요 @storycraft
        //chat.Channel.sendTemplate(new AttachmentTemplate(ReplyAttachment.fromChat(chat), '안녕하세요')); // 답장형식
    }
});

await client.login('123456789@email.com', '123456' /* nice password k*/, 'SHA256 device id');
```

License
-------
node-kakao is following MIT License.

Basic Reference
---------
hallazzang([pykakao](https://github.com/hallazzang/pykakao/))  
ssut([pykakao](https://github.com/ssut/pykakao))  
Cai([0x90 :: Cai's Blog](http://www.bpak.org/blog/))
- [[KakaoTalk+] LOCO 프로토콜 분석 (1)](http://www.bpak.org/blog/2012/12/kakaotalk-loco-프로토콜-분석-1/)
- [[KakaoTalk+] LOCO 프로토콜 분석 (2)](http://www.bpak.org/blog/2012/12/kakaotalk-loco-프로토콜-분석-2/)
- [[KakaoTalk+] LOCO 프로토콜 분석 (3)](http://www.bpak.org/blog/2012/12/kakaotalk-loco-프로토콜-분석-3/)
- [[KakaoTalk+] LOCO 프로토콜 분석 (4)](http://www.bpak.org/blog/2012/12/kakaotalk-loco-프로토콜-분석-4/)
- [[KakaoTalkPC] 카카오톡 PC 버전 분석 (1)](https://www.bpak.org/blog/2013/08/kakaotalkpc-카카오톡-pc-버전-분석-1/)
