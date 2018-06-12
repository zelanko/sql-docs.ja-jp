---
title: XML for Analysis (XMLA) への準拠 |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b618fdd8cca3faed72afb0276f18cd928a3f31f7
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34576884"
---
# <a name="xml-for-analysis-xmla-compliance"></a>XML for Analysis (XMLA) への準拠
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]  

  XML for Analysis 1.1 仕様は、World Wide Web 上に存在するデータ ソースへのアクセスをサポートするオープン スタンダードを記述します。 このトピックでは、XML for Analysis 1.1 仕様 Azure Analysis Services と SQL Server Analysis Services でサポートされている準拠のレベルについて説明します。  
  
## <a name="compliant-items"></a>準拠項目  
Analysis Services は、XML for Analysis 1.1 仕様に表示されるすべての必須項目に準拠します。 さらに、Analysis Services では、XML for Analysis 1.1 仕様で説明されている次の省略可能な項目を実装します。  
  
|アイテム|仕様|実装|  
|----------|-------------------|--------------------|  
|セッション サポート|XML for Analysis 1.1 仕様の「Support for Statefulness in XML for Analysis」セクションに記載されている SOAP ヘッダー要素。|表示されているすべての SOAP ヘッダー要素は、仕様内の説明に従って、Analysis Services でサポートされます。|  
  
## <a name="extensions"></a>拡張機能  
 また、analysis Services は、次の追加機能や機能をサポートするために XML for Analysis 1.1 仕様を拡張します。  
  
|アイテム|仕様|実装|  
|----------|-------------------|--------------------|  
|プロトコル ネゴシエーション|XML for Analysis 1.1 仕様には情報が含まれていません。|プロトコル機能のネゴシエーションをサポートするために Analysis Services によって追加された ProtocolCapabilities ヘッダー要素。|  
|Discover メソッドでサポートされる XML for Analysis (XMLA) コマンド|以下のコマンドが XML for Analysis 1.1 仕様によってサポートされています。<br /><br /> [Statement 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|次のコマンドは、Analysis Services でサポートされます。<br /><br /> [Alter 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [要素をバックアップ&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [要素をバッチ&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [BeginTransaction 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [Cancel 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [ClearCache 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [CommitTransaction 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [要素を作成する&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [Delete 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [DesignAggregations 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Drop 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [要素を挿入&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [要素をロック&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [MergePartitions 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [NotifyTableChange 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [要素を処理&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [Restore 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [RollbackTransaction 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Statement 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [Subscribe 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [Synchronize 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [要素のロック解除&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Update 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [UpdateCells 要素&#40;XMLA&#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|表形式の行セットでの列エラー|XML for Analysis 1.1 仕様にはリストされていません。|[エラー](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)に含まれる列要素のエラーを報告する要素を Analysis Services で使用されて、[行](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)要素。|  
  
## <a name="see-also"></a>参照
 [XML for Analysis (XML for Analysis) リファレンス](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
