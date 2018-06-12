---
title: メソッド (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 15f930695e13d824e70da748dad20cf574e9bc38
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34579144"
---
# <a name="xml-elements---methods"></a>メソッドの XML 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  XML for Analysis (XMLA) プロトコルは、2 つのメソッドを使用して**Discover**と**Execute**アプリケーションが Analysis Services のインスタンスの情報にアクセスするための標準的な方法を提供します。 これらのメソッドは Simple Object Access Protocol (SOAP) を使用して起動されるため、XML 形式の入力を受け入れ、XML 形式の出力を生成します。 Analysis Services では、XML for Analysis 1.1 仕様に準拠して、両方の方法を実装します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、Analysis Services によって実装されている XMLA メソッドについて説明します。  
  
|方法|説明|  
|------------|-----------------|  
|[Discover メソッド&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|Analysis Services のインスタンスから使用可能なデータベースまたは特定のオブジェクトに関する詳細情報の一覧などの情報を取得します。 使用して取得データ、 **Discover**メソッドは渡されたパラメーターの値によって異なります。|  
|[メソッドを実行する&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|XMLA コマンドを Analysis Services のインスタンスに送信されます。 これには、サーバー上のデータの取得や更新など、データ転送に関連した要求が含まれます。|  
  
## <a name="see-also"></a>参照
 [XML 要素&#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML データ型&#40;XMLA&#41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML 要素&#40;XMLA&#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
