## Javascript E𝗺𝗽𝘁𝘆 𝗼𝗯𝗷𝗲𝗰𝘁 𝗮𝘀 𝗮 𝗳𝗮𝗹𝗹𝗯𝗮𝗰𝗸 𝘄𝗵𝗶𝗹𝗲 𝗱𝗲𝘀𝘁𝗿𝘂𝗰𝘁𝘂𝗿𝗶𝗻𝗴

As explained in one of my posts in the Javascript series, you can use the optional chaining operator to simplify and avoid breaking code

So the below code:

```
𝘤𝘰𝘯𝘴𝘵 𝘶𝘴𝘦𝘳 = {
𝘯𝘢𝘮𝘦: '𝘋𝘢𝘷𝘪𝘥'
};

𝘤𝘰𝘯𝘴𝘵 𝘴𝘵𝘳𝘦𝘦𝘵𝘕𝘢𝘮𝘦 = 𝘶𝘴𝘦𝘳.𝘭𝘰𝘤𝘢𝘵𝘪𝘰𝘯 && 𝘶𝘴𝘦𝘳.𝘭𝘰𝘤𝘢𝘵𝘪𝘰𝘯.𝘴𝘵𝘳𝘦𝘦𝘵 && 𝘶𝘴𝘦𝘳.𝘭𝘰𝘤𝘢𝘵𝘪𝘰𝘯.𝘴𝘵𝘳𝘦𝘦𝘵.𝘯𝘢𝘮𝘦;

is same as:

𝘤𝘰𝘯𝘴𝘵 𝘶𝘴𝘦𝘳 = {
𝘯𝘢𝘮𝘦: '𝘋𝘢𝘷𝘪𝘥'
};

𝘤𝘰𝘯𝘴𝘵 𝘴𝘵𝘳𝘦𝘦𝘵𝘕𝘢𝘮𝘦 = 𝘶𝘴𝘦𝘳.𝘭𝘰𝘤𝘢𝘵𝘪𝘰𝘯?.𝘴𝘵𝘳𝘦𝘦𝘵?.𝘯𝘢𝘮𝘦;
``` 
In the above code, 𝘀𝘁𝗿𝗲𝗲𝘁𝗡𝗮𝗺𝗲 will be 𝘂𝗻𝗱𝗲𝗳𝗶𝗻𝗲𝗱 as 𝘀𝘁𝗿𝗲𝗲𝘁 property does not exist on the user object.

This is because the optional chaining operator returns 𝘂𝗻𝗱𝗲𝗳𝗶𝗻𝗲𝗱 if the property does not exist.

And destructuring on 𝘂𝗻𝗱𝗲𝗳𝗶𝗻𝗲𝗱 will throw an error.

So If you're using destructuring along with the optional chaining operator, you will get an uncaught error If you try to use destructuring like this:


```
𝘪𝘧 (𝘶𝘴𝘦𝘳.𝘯𝘢𝘮𝘦) {
𝘤𝘰𝘯𝘴𝘵 { 𝘯𝘢𝘮𝘦, 𝘢𝘥𝘥𝘳𝘦𝘴𝘴 } = 𝘶𝘴𝘦𝘳.𝘭𝘰𝘤𝘢𝘵𝘪𝘰𝘯?.𝘴𝘵𝘳𝘦𝘦𝘵; // 𝙐𝙣𝙘𝙖𝙪𝙜𝙝𝙩 𝙏𝙮𝙥𝙚𝙀𝙧𝙧𝙤𝙧: 𝘾𝙖𝙣𝙣𝙤𝙩 𝙙𝙚𝙨𝙩𝙧𝙪𝙘𝙩𝙪𝙧𝙚 𝙥𝙧𝙤𝙥𝙚𝙧𝙩𝙮 '𝙣𝙖𝙢𝙚' 𝙤𝙛 𝙪𝙣𝙙𝙚𝙛𝙞𝙣𝙚𝙙
}

To fix this, you need to assign an empty object all the time while destructuring like this:

𝘪𝘧 (𝘶𝘴𝘦𝘳.𝘯𝘢𝘮𝘦) {
𝘤𝘰𝘯𝘴𝘵 { 𝘯𝘢𝘮𝘦, 𝘢𝘥𝘥𝘳𝘦𝘴𝘴 } = 𝘶𝘴𝘦𝘳.𝘭𝘰𝘤𝘢𝘵𝘪𝘰𝘯?.𝘴𝘵𝘳𝘦𝘦𝘵 || {}; // 𝙬𝙤𝙧𝙠𝙨 𝙛𝙞𝙣𝙚, 𝙣𝙤 𝙚𝙧𝙧𝙤𝙧
𝘤𝘰𝘯𝘴𝘰𝘭𝘦.𝘭𝘰𝘨(𝘯𝘢𝘮𝘦, 𝘢𝘥𝘥𝘳𝘦𝘴𝘴); // 𝘶𝘯𝘥𝘦𝘧𝘪𝘯𝘦𝘥 𝘶𝘯𝘥𝘦𝘧𝘪𝘯𝘦𝘥
}
``` 
