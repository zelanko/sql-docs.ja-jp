---
title: "文字マップ変換エディター |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.charactermaptransformation.f1
helpviewer_keywords:
- Character Map Transformation Editor
ms.assetid: 3f1dbcf9-9cca-4606-bdcc-7ea6ad48cdf3
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1ddabff7405401657b44a4cbc9205cf6092949d7
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="character-map-transformation-editor"></a>文字マップ変換エディター
  **[文字マップ変換エディター]** ダイアログ ボックスを使用すると、列のデータに適用する文字列関数を選択し、マッピングが埋め込み先の変更か新しい列として追加されるかを指定できます。  
  
 文字マップ変換の詳細については、「 [Character Map Transformation](../../../integration-services/data-flow/transformations/character-map-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **使用できる入力列**  
 チェック ボックスを使用し、文字列関数を使用して変換する列を選択します。 選択は下の表に表示されます。  
  
 **入力列**  
 上の表で選択された入力列が表示されます。 使用できる入力列の一覧を使用して、選択した列を変更したり、削除したりできます。  
  
 **転送先**  
 文字列処理の結果を、既定の列を使用して所定の場所に保存するか、変更されたデータを新しい列として保存するかを指定します。  
  
|値|Description|  
|-----------|-----------------|  
|[新しい列]|データを新しい列に保存します。 **[出力の別名]**で、列名を割り当てます。|  
|[埋め込み先変更]|変更されたデータを既存の列に保存します。|  
  
 **操作**  
 列のデータに適用する文字列関数を一覧から選択します。  
  
|値|Description|  
|-----------|-----------------|  
|小文字|小文字に変換します。|  
|大文字|大文字に変換します。|  
|バイトの反転|バイト順序を反転します。|  
|ひらがな|カタカナをひらがなに変換します。|  
|カタカナ|ひらがなをカタカナに変換します。|  
|半角|全角文字を半角文字に変換します。|  
|全角|半角文字を全角文字に変換します。|  
|言語の文字種|システムのルールではなく、言語の文字種による規則 (チュルク語などのロケールにおける Unicode の文字種の単純な割り当て) を適用します。|  
|簡体字中国語|繁体字中国語の文字を簡体字中国語に変換します。|  
|繁体字中国語|簡体字中国語の文字を繁体字中国語に変換します。|  
  
 **[出力の別名]**  
 各出力列の別名を入力します。 既定では、入力列の名前の後に " **のコピー** " が追加された別名になりますが、固有のわかりやすい名前を選択することもできます。  
  
 **エラー出力の構成**  
 [[エラー出力の構成]](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) ダイアログ ボックスを使用して、この変換のエラー処理オプションを指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  
