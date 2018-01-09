---
title: "XML for Analysis への準拠 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: "15"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: efd2d4cfd7adb6185abdd383a261494495817ec5
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="xml-for-analysis-compliance-xmla"></a>XML for Analysis への準拠 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]XML for Analysis 1.1 仕様では、World Wide Web 上に存在するデータ ソースへのデータ アクセスをサポートするオープン スタンダードについて説明します。 このトピックの詳細レベルでサポートされている XML for Analysis 1.1 仕様に準拠して[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。  
  
## <a name="compliant-items"></a>準拠項目  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、XML for Analysis 1.1 仕様にリストされたすべての必須項目に準拠しています。 それに加えて、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XML for Analysis 1.1 仕様に記述された以下のオプション項目を実装しています。  
  
|アイテム|仕様|実装|  
|----------|-------------------|--------------------|  
|セッション サポート|XML for Analysis 1.1 仕様の「Support for Statefulness in XML for Analysis」セクションに記載されている SOAP ヘッダー要素。|リストされているすべての SOAP ヘッダー要素は、仕様に記述されているとおりに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でサポートされます。|  
  
## <a name="extensions"></a>拡張機能  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XML for Analysis 1.1 仕様の拡張機能として、次のような追加機能も提供します。  
  
|アイテム|仕様|実装|  
|----------|-------------------|--------------------|  
|プロトコル ネゴシエーション|XML for Analysis 1.1 仕様には情報が含まれていません。|によって追加された ProtocolCapabilities ヘッダー要素[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロトコル機能のネゴシエーションをサポートするためにします。|  
|Discover メソッドでサポートされる XML for Analysis (XMLA) コマンド|以下のコマンドが XML for Analysis 1.1 仕様によってサポートされています。<br /><br /> [Statement 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)|以下のコマンドが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってサポートされています。<br /><br /> [Alter 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)<br /><br /> [Backup 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/backup-element-xmla.md)<br /><br /> [バッチ要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)<br /><br /> [BeginTransaction 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)<br /><br /> [要素 &#40; [キャンセル] します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/cancel-element-xmla.md)<br /><br /> [ClearCache 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md)<br /><br /> [CommitTransaction 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)<br /><br /> [要素 &#40; を作成します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)<br /><br /> [要素 &#40; を削除します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/delete-element-xmla.md)<br /><br /> [DesignAggregations 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md)<br /><br /> [Drop 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/drop-element-xmla.md)<br /><br /> [要素 &#40; を挿入します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/insert-element-xmla.md)<br /><br /> [Lock 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)<br /><br /> [MergePartitions 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)<br /><br /> [NotifyTableChange 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/notifytablechange-element-xmla.md)<br /><br /> [Process 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)<br /><br /> [要素 &#40; を復元します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)<br /><br /> [RollbackTransaction 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)<br /><br /> [Statement 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/statement-element-xmla.md)<br /><br /> [要素 &#40; を定期受信します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/subscribe-element-xmla.md)<br /><br /> [要素 &#40; を同期します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)<br /><br /> [要素 &#40; をロック解除します。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/unlock-element-xmla.md)<br /><br /> [Update 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/update-element-xmla.md)<br /><br /> [UpdateCells 要素 &#40;です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/updatecells-element-xmla.md)|  
|表形式の行セットでの列エラー|XML for Analysis 1.1 仕様にはリストされていません。|[エラー](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)要素はによって使用[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に含まれる列要素のエラーを報告する、[行](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)要素。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis (XML for Analysis) リファレンス](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
