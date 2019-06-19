---
title: 挿入、更新、およびメンバー (XMLA) の削除 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a409e21e925b3912aee5ec751747f61bce05276
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63138584"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>メンバーの挿入、更新、および削除 (XMLA)
  使用することができます、[挿入](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)、[更新](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)、および[ドロップ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)コマンドでは、XML for Analysis (XMLA) それぞれを挿入するには、更新、またはメンバーを書き込み許可ディメンションから削除します。 書き込み許可ディメンションの詳細については、次を参照してください。 [Write-Enabled ディメンション](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)します。  
  
## <a name="inserting-new-members"></a>新しいメンバーの挿入  
 **挿入**コマンドは、書き込み許可ディメンション内の指定された属性に新しいメンバーを挿入します。  
  
 作成する前に、**挿入**コマンドを挿入する新しいメンバーに対して使用可能な次の情報が必要があります。  
  
-   新しいメンバーを挿入するディメンション。  
  
-   新しいメンバーを挿入するディメンションの属性。  
  
-   新しいメンバーの名前。ある場合は、名前の翻訳も含みます。  
  
-   新しいメンバーのキー。 属性で複合キーを使用する場合は、キーに複数の値が必要になることがあります。  
  
-   ディメンション内で他の属性として実装されていない属性プロパティがあれば、その値。 そのような属性プロパティには、単項演算子、翻訳、カスタム ロールアップ、カスタム ロールアップ プロパティ、およびスキップされたレベルなどがあります。  
  
 **挿入**コマンドは、2 つのプロパティ。  
  
-   [オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)プロパティで、メンバーが挿入されるのディメンションのオブジェクト参照が含まれています。 オブジェクト参照には、そのディメンションに関するデータベース識別子、キューブ識別子、およびディメンション識別子が含まれます。  
  
-   [属性](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla)プロパティで、1 つ以上含む[属性](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla)メンバーの挿入する属性を識別する要素。 各**属性**要素属性を識別する名前、値、翻訳、単項演算子、カスタム ロールアップ、カスタム ロールアップ プロパティを提供し、指定した属性に追加する 1 つのメンバーのレベルをスキップします。  
  
    > [!NOTE]  
    >  すべてのプロパティ、**属性**要素を含める必要があります。 そうでない場合、エラーが発生する可能性があります。  
  
## <a name="updating-existing-members"></a>既存のメンバーの更新  
 **Update**コマンドは、書き込み許可ディメンション内の他の属性内の他のメンバーとの関係に基づいて、指定した属性の既存のメンバーを更新します。 **Update**階層内の他のレベルにメンバーが、ディメンションに含まれているし、親属性で定義されている親子階層を再構築に使用できるコマンドを移動できます。  
  
 作成する前に、 **Update**コマンドを更新するメンバーの使用可能な次の情報が必要があります。  
  
-   更新する既存のメンバーを含むディメンション。  
  
-   更新する既存のメンバーを含むディメンションの属性。  
  
-   既存のメンバーのキー。 属性で複合キーを使用する場合は、キーに複数の値が必要になることがあります。  
  
-   ディメンション内で他の属性として実装されていない属性プロパティがあれば、その値。 そのような属性プロパティには、単項演算子、翻訳、カスタム ロールアップ、カスタム ロールアップ プロパティ、およびスキップされたレベルなどがあります。  
  
 **Update**コマンドは、3 つだけの必須プロパティ。  
  
-   **オブジェクト**プロパティを更新するか、メンバー、ディメンションのオブジェクト参照が含まれています。 オブジェクト参照には、そのディメンションに関するデータベース識別子、キューブ識別子、およびディメンション識別子が含まれます。  
  
-   **属性**プロパティで、1 つ以上含む**属性**メンバーの更新する属性を識別する要素。 **属性**要素属性を識別する名前、値、翻訳、単項演算子、カスタム ロールアップ、カスタム ロールアップ プロパティを提供およびスキップされたレベルを 1 つのメンバーが、指定した属性の更新の。  
  
    > [!NOTE]  
    >  すべてのプロパティ、**属性**要素を含める必要があります。 そうでない場合、エラーが発生する可能性があります。  
  
-   [場所](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla)プロパティで、1 つ以上含む**属性**メンバーの更新する属性を制限する要素。 **場所**プロパティは、制限するために重要、 **Update**メンバーの特定のインスタンスにコマンド。 場合、**場所**プロパティが指定されていない、指定されたメンバーのすべてのインスタンスが更新されます。 たとえば、3 人の顧客について、都市名を Redmond から Bellevue に変更したいとします。 市区町村名を変更することを提供する必要があります、**場所**プロパティを顧客に 3 つのメンバーを識別する属性、City 属性のメンバーを変更する必要があります。 これを指定しない場合**場所**プロパティ、すべての顧客が現在 Redmond である市区町村名前を持つ必要があります、都市名が bellevue に変更、 **Update**コマンドを実行します。  
  
    > [!NOTE]  
    >  新しいメンバーを除く、**更新**コマンドに含まれていない属性の属性のキー値で更新できる、**場所**句。 たとえば、ある顧客が更新されている場合には都市名を更新できません。それ以外の場合には、すべての顧客に関して都市名が変更されます。  
  
### <a name="updating-members-in-parent-attributes"></a>親階層のメンバーの更新  
 親の属性をサポートするために、 **Update**省略可能なコマンド[MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)MovewithDescedants プロパティ。 設定、 **MoveWithDescendants**プロパティを true には、親メンバーの子孫の必要がありますも移動すること、親メンバーとその親メンバーの識別子が変更されたときを示します。 この値が false に設定されている場合は、親メンバーを移動すると、その親メンバーの直接の子孫が親メンバーのあったレベルに昇格します。  
  
 親属性内のメンバーを更新するときに、**更新**コマンドは、その他の属性のメンバーを更新できません。  
  
## <a name="dropping-existing-members"></a>既存のメンバーの削除  
 作成する前に、**ドロップ**コマンドを削除するメンバーの使用可能な次の情報が必要があります。  
  
-   削除する既存のメンバーを含むディメンション。  
  
-   削除する既存のメンバーを含むディメンションの属性。  
  
-   削除する既存のメンバーのキー。 属性で複合キーを使用する場合は、キーに複数の値が必要になることがあります。  
  
 **ドロップ**コマンドは、2 つの必須プロパティ。  
  
-   **オブジェクト**プロパティで、メンバーが削除されるディメンションのオブジェクト参照が含まれています。 オブジェクト参照には、そのディメンションに関するデータベース識別子、キューブ識別子、およびディメンション識別子が含まれます。  
  
-   **場所**プロパティで、1 つ以上含む**属性**メンバーの削除する属性を制限する要素。 **場所**プロパティは、制限するために重要、**ドロップ**メンバーの特定のインスタンスにコマンド。 場合、**場所**コマンドが指定されていない、指定されたメンバーのすべてのインスタンスが削除されます。 たとえば、Redmond から 3 人の顧客を削除したいとします。 これらの顧客を削除するには指定する必要があります、**場所**Customer 属性の 3 つのメンバーを削除して、3 人の顧客の削除元 City 属性の Redmond メンバーを識別するプロパティ。 場合、**場所**プロパティには、City 属性の Redmond メンバーのみを指定します、Redmond に関連付けられているすべての顧客が削除されます。、**ドロップ**コマンド。 場合、**場所**、Customer 属性でプロパティが 3 つのメンバーにのみを指定します、3 人の顧客が完全に削除、**ドロップ**コマンド。  
  
    > [!NOTE]  
    >  **属性**に含まれる要素を**ドロップ**のみコマンドを含める必要があります、 **AttributeName**と**キー**プロパティ。 そうでない場合、エラーが発生する可能性があります。  
  
### <a name="dropping-members-in-parent-attributes"></a>親階層のメンバーの削除  
 設定、 [DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla)プロパティは親メンバーの子孫が親メンバーを削除するかも示します。 この値が false に設定されている場合は、その親メンバーの直接の子孫が、親メンバーのあったレベルに昇格します。  
  
> [!IMPORTANT]  
>  親メンバーとその子孫の両方を削除するためにユーザーに必要な権限は、親メンバーに対する削除権限だけです。 ユーザーが子孫に対する削除権限を持っている必要はありません。  
  
## <a name="see-also"></a>参照  
 [Drop 要素&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)   
 [要素を挿入&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)   
 [Update 要素&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [定義するオブジェクトを識別したり&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)   
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
