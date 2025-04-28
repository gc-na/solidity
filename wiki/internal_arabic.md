<!--
Meta Description: # استخدام الكلمة المحجوزة "internal" في Solidity ## ملخص تُستخدم الكلمة المحجوزة "internal" في لغة Solidity لتحديد مستوى الوصول إلى المتغيرات والدوال ...
Meta Keywords: internal, الوصول, solidity, إلى, استخدام
-->

# استخدام الكلمة المحجوزة "internal" في Solidity

## ملخص
تُستخدم الكلمة المحجوزة "internal" في لغة Solidity لتحديد مستوى الوصول إلى المتغيرات والدوال داخل العقود الذكية. هذا النوع من الوصول يتيح للعقود الفرعية الوصول إلى مكونات العقد الأصلية، مما يعزز من قابلية إعادة الاستخدام والتوسع في الكود.

## الوثائق
### الغرض
تُعتبر "internal" واحدة من ثلاثة مستويات وصول متاحة في Solidity، إلى جانب "public" و"private". تُحدد "internal" أن العناصر المعنونة بها يمكن الوصول إليها فقط من داخل العقد نفسه أو من العقود المشتقة منه.

### الاستخدام
يمكن استخدام "internal" مع المتغيرات والدوال على حدٍ سواء. عند استخدام هذه الكلمة المحجوزة، فإنها تحمي البيانات من الوصول الخارجي، مما يساعد على الحفاظ على أمان العقد.

#### الصيغة الأساسية
```solidity
contract MyContract {
    uint internal myVariable;

    function myFunction() internal {
        // تنفيذ الكود
    }
}
```

## الأمثلة
### مثال 1: استخدام "internal" مع المتغيرات
```solidity
pragma solidity ^0.8.0;

contract Base {
    uint internal internalVariable;

    function setInternalVariable(uint _value) internal {
        internalVariable = _value;
    }
}

contract Derived is Base {
    function updateVariable(uint _value) public {
        setInternalVariable(_value);
    }
}
```

### مثال 2: استخدام "internal" مع الدوال
```solidity
pragma solidity ^0.8.0;

contract Base {
    function internalFunction() internal pure returns (string memory) {
        return "هذه دالة داخلية!";
    }
}

contract Derived is Base {
    function callInternalFunction() public view returns (string memory) {
        return internalFunction();
    }
}
```

## الشرح
### النقاط الشائعة التي يجب الانتباه إليها
- **الوصول المحدود**: لا يمكن الوصول إلى العناصر المعنونة بـ "internal" من خارج العقد أو العقود المشتقة، لذا يجب التخطيط جيدًا لاستخدامها.
- **تجنب الأخطاء**: إذا حاولت الوصول إلى عنصر "internal" من عقد غير مشتق، سيؤدي ذلك إلى حدوث خطأ في الترجمة.
- **استخدامها بحكمة**: يُفضل استخدام "internal" عندما تحتاج إلى حماية البيانات أو الدوال من الوصول الخارجي ولكن تحتاج إلى توفير الوصول للعقود المشتقة.

## ملخص بجملة واحدة
تتيح الكلمة المحجوزة "internal" في Solidity الوصول إلى المتغيرات والدوال فقط من داخل العقد نفسه أو من العقود المشتقة، مما يعزز من أمان ومرونة الكود.