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
ms.openlocfilehash: f42c986f8ebb3be2126335663a0716049e908ab0
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="xml-elements---methods"></a>メソッドの XML 要素
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  XML for Analysis (XMLA) プロトコルは、2 つのメソッドを使用して**Discover**と**Execute**、アプリケーションのインスタンスの情報にアクセスするための標準的な方法を提供する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]. これらのメソッドは Simple Object Access Protocol (SOAP) を使用して起動されるため、XML 形式の入力を受け入れ、XML 形式の出力を生成します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XML for Analysis 1.1 仕様に準拠して、この 2 つのメソッドを実装しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 以下のトピックは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって実装されている XMLA メソッドについて説明しています。  
  
|方法|Description|  
|------------|-----------------|  
|[Discover メソッド&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-discover.md)|使用可能なデータベースの一覧や特定のオブジェクトの詳細などの情報を、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスから取得します。 使用して取得データ、 **Discover**メソッドは渡されたパラメーターの値によって異なります。|  
|[メソッドを実行する&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-methods-execute.md)|XMLA コマンドを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに送信します。 これには、サーバー上のデータの取得や更新など、データ転送に関連した要求が含まれます。|  
  
## <a name="see-also"></a>参照  
 [XML 要素 & #40 です。XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML データ型 & #40 です。XMLA & #41;](../../analysis-services/xmla/xml-data-types/xml-data-types-xmla.md)   
 [XML 要素 & #40 です。XMLA & #41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)  
  
  
