<!--
Meta Description: # الماب (Mapping) في لغة Solidity: الدليل الشامل ## ملخص الماب هو نوع من البيانات في لغة Solidity يُستخدم لتخزين القيم المرتبطة بمفاتيح فريدة، مما يُت...
Meta Keywords: الماب, solidity, القيم, public, uint
-->

# الماب (Mapping) في لغة Solidity: الدليل الشامل

## ملخص
الماب هو نوع من البيانات في لغة Solidity يُستخدم لتخزين القيم المرتبطة بمفاتيح فريدة، مما يُتيح إنشاء هياكل بيانات مرنة وسهلة الاستخدام في العقود الذكية.

## الوثائق
### الغرض
يُستخدم الماب في Solidity لتخزين البيانات بطريقة تجعل الوصول إليها سريعًا وفعالًا. يعمل الماب كجدول بحث (hash table)، حيث يُمكن تخزين قيمة مرتبطة بمفتاح فريد، مما يُسهل إدارة مجموعة كبيرة من البيانات.

### الاستخدام
يمكن تعريف الماب باستخدام الصيغة التالية:
```solidity
mapping(KeyType => ValueType) public mapName;
```
- **KeyType**: نوع المفتاح (مثل `address`، `uint`، إلخ).
- **ValueType**: نوع القيمة التي سيتم تخزينها (مثل `uint`، `string`، إلخ).
- **mapName**: اسم الماب.

### التفاصيل
- يتم الوصول إلى القيم المخزنة في الماب باستخدام المفتاح المحدد.
- إذا تم محاولة الوصول إلى مفتاح غير موجود، سيتم إرجاع القيمة الافتراضية لنوع القيم.
- يمكن استخدام الماب لتخزين بيانات معقدة، مثل هياكل البيانات (structs).

## أمثلة
### مثال 1: ماب بسيط لتخزين الأرصدة
```solidity
pragma solidity ^0.8.0;

contract SimpleBank {
    mapping(address => uint) public balances;

    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }

    function getBalance() public view returns (uint) {
        return balances[msg.sender];
    }
}
```

### مثال 2: ماب لتخزين معلومات المستخدمين
```solidity
pragma solidity ^0.8.0;

contract UserRegistry {
    struct User {
        string name;
        uint age;
    }

    mapping(address => User) public users;

    function register(string memory _name, uint _age) public {
        users[msg.sender] = User(_name, _age);
    }

    function getUserInfo() public view returns (string memory, uint) {
        User memory user = users[msg.sender];
        return (user.name, user.age);
    }
}
```

## الشرح
### النقاط الشائعة
- **القيم الافتراضية**: عند الوصول إلى مفتاح غير موجود في الماب، سيتم إرجاع القيمة الافتراضية لنوع القيمة (مثل `0` للأعداد، أو سلسلة فارغة للنصوص).
- **عدم إمكانية التكرار**: لا يمكن استخدام الماب في الحلقات أو التكرار (iterable) بشكل مباشر، مما يعني أنه لا يمكن استعراض جميع المفاتيح أو القيم المخزنة.
- **يجب الحذر عند استخدام المابس**: لا تُستخدم المابس بشكل مباشر في الدوال التي تتطلب تعيين القيم أو تعديل البيانات.

## ملخص في جملة واحدة
الماب في Solidity هو هيكل بيانات فعال لتخزين القيم المرتبطة بمفاتيح فريدة، مما يُسهل إدارة البيانات في العقود الذكية.