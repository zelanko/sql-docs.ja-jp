---
title: 挿入、更新、およびメンバー (XMLA) の削除 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f80756cb147b33b7caede48093fb69e17eb4a263
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>メンバーの挿入、更新、および削除 (XMLA)
  使用することができます、[挿入](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)、[更新](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)、および[ドロップ](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)コマンド XML for Analysis (XMLA) それぞれを挿入するには、更新、またはメンバーを書き込み許可ディメンションから削除します。 書き込み許可ディメンションの詳細については、次を参照してください。 [Write-Enabled ディメンション](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)です。  
  
## <a name="inserting-new-members"></a>新しいメンバーの挿入  
 **挿入**コマンドは、書き込み許可ディメンション内の指定した属性に新しいメンバーを挿入します。  
  
 作成する前に、**挿入**コマンドを挿入する新しいメンバーに対して使用可能な次の情報を用意する必要があります。  
  
-   新しいメンバーを挿入するディメンション。  
  
-   新しいメンバーを挿入するディメンションの属性。  
  
-   新しいメンバーの名前。ある場合は、名前の翻訳も含みます。  
  
-   新しいメンバーのキー。 属性で複合キーを使用する場合は、キーに複数の値が必要になることがあります。  
  
-   ディメンション内で他の属性として実装されていない属性プロパティがあれば、その値。 そのような属性プロパティには、単項演算子、翻訳、カスタム ロールアップ、カスタム ロールアップ プロパティ、およびスキップされたレベルなどがあります。  
  
 **挿入**コマンドは 2 つのプロパティを取得します。  
  
-   [オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)プロパティで、メンバーが挿入するのには、ディメンションのオブジェクト参照が含まれています。 オブジェクト参照には、そのディメンションに関するデータベース識別子、キューブ識別子、およびディメンション識別子が含まれます。  
  
-   [属性](../../analysis-services/xmla/xml-elements-properties/attributes-element-xmla.md)プロパティで、1 つ以上含む[属性](../../analysis-services/xmla/xml-elements-properties/attribute-element-xmla.md)メンバーを挿入する属性を識別する要素。 各**属性**要素、属性を識別名、値、翻訳、単項演算子、カスタム ロールアップ、カスタム ロールアップ プロパティを提供およびスキップされたレベルを指定した属性に追加する 1 つのメンバーです。  
  
    > [!NOTE]  
    >  すべてのプロパティ、**属性**要素を含める必要があります。 そうでない場合、エラーが発生する可能性があります。  
  
## <a name="updating-existing-members"></a>既存のメンバーの更新  
 **更新**コマンドは、書き込み許可ディメンション内の他の属性の他のメンバーとの関係に基づいて、指定した属性の既存のメンバーを更新します。 **更新**階層内の他のレベルにメンバーが、ディメンションに含まれているし、親属性で定義されている親子階層を再構築に使用できるコマンドを移動できます。  
  
 作成する前に、**更新**コマンドを更新するメンバーの使用可能な次の情報を持つ必要があります。  
  
-   更新する既存のメンバーを含むディメンション。  
  
-   更新する既存のメンバーを含むディメンションの属性。  
  
-   既存のメンバーのキー。 属性で複合キーを使用する場合は、キーに複数の値が必要になることがあります。  
  
-   ディメンション内で他の属性として実装されていない属性プロパティがあれば、その値。 そのような属性プロパティには、単項演算子、翻訳、カスタム ロールアップ、カスタム ロールアップ プロパティ、およびスキップされたレベルなどがあります。  
  
 **更新**コマンドは 3 つだけ必要なプロパティを取得します。  
  
-   **オブジェクト**プロパティで、更新するか、メンバー、ディメンションのオブジェクト参照が含まれています。 オブジェクト参照には、そのディメンションに関するデータベース識別子、キューブ識別子、およびディメンション識別子が含まれます。  
  
-   **属性**プロパティで、1 つ以上含む**属性**メンバーを更新する属性を識別する要素。 **属性**要素、属性を識別名、値、翻訳、単項演算子、カスタム ロールアップ、カスタム ロールアップ プロパティを提供およびスキップされたレベルを 1 つのメンバーが、指定した属性が更新されました。  
  
    > [!NOTE]  
    >  すべてのプロパティ、**属性**要素を含める必要があります。 そうでない場合、エラーが発生する可能性があります。  
  
-   [場所](../../analysis-services/xmla/xml-elements-properties/where-element-xmla.md)プロパティで、1 つ以上含む**属性**メンバーを更新する属性を制限する要素。 **場所**プロパティは使用を制限するために重要、**更新**メンバーの特定のインスタンスにコマンド。 場合、**場所**プロパティが指定されていない指定されたメンバーのすべてのインスタンスが更新されます場合、。 たとえば、3 人の顧客について、都市名を Redmond から Bellevue に変更したいとします。 指定する必要があります、市区町村名を変更するには**場所**City 属性のメンバーを変更するため、お客様の 3 つのメンバーを識別するプロパティの属性です。 これを指定しない場合**場所**プロパティが現在 Redmond である市区町村名前を持つすべてのお客様には、都市名が bellevue に変更、**更新**コマンドを実行します。  
  
    > [!NOTE]  
    >  新しいメンバーの場合、**更新**コマンドに含まれていない属性に対する属性のキー値で更新できる、**場所**句。 たとえば、ある顧客が更新されている場合には都市名を更新できません。それ以外の場合には、すべての顧客に関して都市名が変更されます。  
  
### <a name="updating-members-in-parent-attributes"></a>親階層のメンバーの更新  
 親属性をサポートするために、**更新**省略可能なコマンド[MoveWithDescendants](../../analysis-services/xmla/xml-elements-properties/movewithdescendants-element-xmla.md)MovewithDescedants プロパティです。 設定、 **MoveWithDescendants**プロパティを true には、親メンバーの子孫も移動する必要、親メンバーとその親メンバーの識別子が変更されたときに示します。 この値が false に設定されている場合は、親メンバーを移動すると、その親メンバーの直接の子孫が親メンバーのあったレベルに昇格します。  
  
 親属性のメンバーを更新するときに、**更新**コマンドは、その他の属性のメンバーを更新できません。  
  
## <a name="dropping-existing-members"></a>既存のメンバーの削除  
 作成する前に、**ドロップ**コマンドを削除するメンバーの使用可能な次の情報を用意する必要があります。  
  
-   削除する既存のメンバーを含むディメンション。  
  
-   削除する既存のメンバーを含むディメンションの属性。  
  
-   削除する既存のメンバーのキー。 属性で複合キーを使用する場合は、キーに複数の値が必要になることがあります。  
  
 **ドロップ**コマンドは 2 つだけ必要なプロパティを取得します。  
  
-   **オブジェクト**プロパティで、メンバーがドロップされるディメンションのオブジェクト参照が含まれています。 オブジェクト参照には、そのディメンションに関するデータベース識別子、キューブ識別子、およびディメンション識別子が含まれます。  
  
-   **場所**プロパティで、1 つ以上含む**属性**メンバーを削除する属性を制限する要素。 **場所**プロパティは使用を制限するために重要、**ドロップ**メンバーの特定のインスタンスにコマンド。 場合、**場所**コマンドが指定されていない指定されたメンバーのすべてのインスタンスが削除されます場合、。 たとえば、Redmond から 3 人の顧客を削除したいとします。 これらの顧客を削除する必要がありますを入力して、**場所**Customer 属性の 3 つのメンバーを削除して元の 3 人の顧客は、削除する City 属性の Redmond メンバーを識別するプロパティです。 場合、**場所**プロパティには、City 属性の Redmond メンバーのみを指定します、Redmond に関連付けられているすべての顧客が削除されます。、**ドロップ**コマンド。 場合、**場所**プロパティは、Customer 属性で 3 つのメンバーのみを指定、3 人の顧客を完全に削除されてしまいます、**ドロップ**コマンド。  
  
    > [!NOTE]  
    >  **属性**要素に含まれる、**ドロップ**のみコマンドを含める必要があります、 **AttributeName**と**キー**プロパティです。 そうでない場合、エラーが発生する可能性があります。  
  
### <a name="dropping-members-in-parent-attributes"></a>親階層のメンバーの削除  
 設定、 [DeleteWithDescendants](../../analysis-services/xmla/xml-elements-properties/deletewithdescendants-element-xmla.md)プロパティは、親メンバーの子孫は親メンバーとも削除する必要がありますを示します。 この値が false に設定されている場合は、その親メンバーの直接の子孫が、親メンバーのあったレベルに昇格します。  
  
> [!IMPORTANT]  
>  親メンバーとその子孫の両方を削除するためにユーザーに必要な権限は、親メンバーに対する削除権限だけです。 ユーザーが子孫に対する削除権限を持っている必要はありません。  
  
## <a name="see-also"></a>参照  
 [Drop 要素 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)   
 [要素 & #40; を挿入します。XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)   
 [Update 要素 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)   
 [定義するオブジェクトを識別したり&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)   
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
