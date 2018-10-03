---
title: メソッド (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
topic_type:
- apiref
- apinav
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#
helpviewer_keywords:
- methods [XML for Analysis]
- XML for Analysis, methods
- XMLA, methods
ms.assetid: c6768dd4-ca06-4a85-93b7-5fd5700886ad
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1e073eae6637b726a473ea7bf95057ed1548982
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48088592"
---
# <a name="methods-xmla"></a>メソッド (XMLA)
  XML for Analysis (XMLA) プロトコルは 2 つのメソッドを使用して`Discover`と`Execute`、アプリケーションのインスタンスの情報にアクセスするための標準的な方法を提供する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。 これらのメソッドは Simple Object Access Protocol (SOAP) を使用して起動されるため、XML 形式の入力を受け入れ、XML 形式の出力を生成します。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XML for Analysis 1.1 仕様に準拠して、この 2 つのメソッドを実装しています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 以下のトピックは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によって実装されている XMLA メソッドについて説明しています。  
  
|方法|説明|  
|------------|-----------------|  
|[Discover メソッド&#40;XMLA&#41;](xml-elements-methods-discover.md)|使用可能なデータベースの一覧や特定のオブジェクトの詳細などの情報を、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスから取得します。 `Discover` メソッドを使用して取得されるデータは、メソッドに渡されるパラメーターの値によって異なります。|  
|[Execute メソッド&#40;XMLA&#41;](xml-elements-methods-execute.md)|XMLA コマンドを [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに送信します。 これには、サーバー上のデータの取得や更新など、データ転送に関連した要求が含まれます。|  
  
## <a name="see-also"></a>参照  
 [XML 要素&#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)   
 [XML データ型&#40;XMLA&#41;](xml-data-types/xml-data-types-xmla.md)   
 [XML 要素&#40;XMLA&#41;](../dev-guide/xml-elements-xmla.md)  
  
  
