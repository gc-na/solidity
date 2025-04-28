<!--
Meta Description: # استخدام الأمر "import" في لغة Solidity ## ملخص الأمر "import" في لغة Solidity يُستخدم لإدراج ملفات أو مكتبات أخرى داخل كود العقد الذكي، مما يُتيح لك...
Meta Keywords: import, solidity, sol, استيراد, الأمر
-->

# استخدام الأمر "import" في لغة Solidity

## ملخص
الأمر "import" في لغة Solidity يُستخدم لإدراج ملفات أو مكتبات أخرى داخل كود العقد الذكي، مما يُتيح لك إعادة استخدام الكود وتنظيم المشاريع بشكل أفضل.

## الوثائق
### الهدف
غرض الأمر "import" هو تسهيل عملية إدارة الكود عن طريق السماح للمطورين باستيراد مكتبات أو عقود ذكية أخرى، مما يقلل من تكرار الكود ويساعد في بناء تطبيقات مرنة وقابلة للتوسع.

### الاستخدام
يتم استخدام الأمر "import" في بداية ملف Solidity ويمكن أن يتضمن مسارًا نسبيًا أو مطلقًا للملف المراد استيراده. يمكن استيراد ملفات تحتوي على عقود أو مكتبات أو حتى واجهات. 

### التفاصيل
- **صياغة الأمر**: 
  ```solidity
  import "path/to/File.sol";
  ```
- **استيراد مكتبة**:
  ```solidity
  import "path/to/Library.sol";
  ```
- **استيراد واجهة**:
  ```solidity
  import "path/to/Interface.sol";
  ```

يمكنك استيراد عدة ملفات في نفس الوقت باستخدام الفاصلة:
```solidity
import "Path1.sol", "Path2.sol";
```

## الأمثلة
### مثال 1: استيراد عقد بسيط
```solidity
// MyContract.sol
import "./OtherContract.sol";

contract MyContract {
    OtherContract private otherContract;

    constructor(address _otherContractAddress) {
        otherContract = OtherContract(_otherContractAddress);
    }
}
```

### مثال 2: استيراد مكتبة
```solidity
// MyLibrary.sol
library MyLibrary {
    function add(uint a, uint b) internal pure returns (uint) {
        return a + b;
    }
}

// UsingLibrary.sol
import "./MyLibrary.sol";

contract UsingLibrary {
    function useAdd(uint a, uint b) public pure returns (uint) {
        return MyLibrary.add(a, b);
    }
}
```

## الشرح
### الأخطاء الشائعة
- **عدم وجود الملف**: تأكد من أن مسار الملف صحيح وأن الملف موجود في المكان المحدد.
- **الأذونات**: تأكد من أن لديك الأذونات الصحيحة للوصول إلى الملفات المستوردة.
- **تعارض الأسماء**: في حالة استيراد ملفات تحتوي على عناصر بنفس الاسم، قد يحدث تعارض. استخدم "as" لتجنب ذلك.

### ملاحظات إضافية
- يُفضل استخدام مسارات نسبية لتسهيل إدارة الملفات داخل المشاريع الكبيرة.
- قم بترتيب الاستيرادات بحسب الأهمية أو الاستخدام لتسهيل القراءة.

## ملخص جملة واحدة
الأمر "import" في Solidity يُستخدم لاستيراد ملفات أو مكتبات أخرى، مما يُساعد في تنظيم الكود وإعادة استخدامه بفعالية.