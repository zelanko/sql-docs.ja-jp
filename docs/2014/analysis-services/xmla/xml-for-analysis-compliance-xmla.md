---
title: XML for Analysis への準拠 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- compliance [XML for Analysis]
- XML for Analysis, compliance
- XMLA, extended functionality
- XML for Analysis, extended functionality
- XMLA, compliance
- extending XML for Analysis
ms.assetid: d987d320-5581-4454-ad45-68e3a22175b6
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cc7a8da77b72f25a68764636fbe15bc2d9e4ae04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37267088"
---
# <a name="xml-for-analysis-compliance-xmla"></a>XML for Analysis への準拠 (XMLA)
  XML for Analysis 1.1 仕様は、World Wide Web 上に存在するデータ ソースへのアクセスをサポートするオープン スタンダードを記述します。 このトピックでサポートされている XML for Analysis 1.1 仕様への準拠のレベルの詳細を[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]します。  
  
## <a name="compliant-items"></a>準拠項目  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、XML for Analysis 1.1 仕様にリストされたすべての必須項目に準拠しています。 それに加えて、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XML for Analysis 1.1 仕様に記述された以下のオプション項目を実装しています。  
  
|アイテム|仕様|実装|  
|----------|-------------------|--------------------|  
|セッション サポート|XML for Analysis 1.1 仕様の「Support for Statefulness in XML for Analysis」セクションに記載されている SOAP ヘッダー要素。|リストされているすべての SOAP ヘッダー要素は、仕様に記述されているとおりに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でサポートされます。|  
  
## <a name="extensions"></a>拡張機能  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は XML for Analysis 1.1 仕様の拡張機能として、次のような追加機能も提供します。  
  
|アイテム|仕様|実装|  
|----------|-------------------|--------------------|  
|プロトコル ネゴシエーション|XML for Analysis 1.1 仕様には情報が含まれていません。|[ProtocolCapabilities](xml-elements-headers/protocolcapabilities-element-xmla.md)によって追加されたヘッダー要素[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロトコル機能のネゴシエーションをサポートするためにします。|  
|Discover メソッドでサポートされる XML for Analysis (XMLA) コマンド|以下のコマンドが XML for Analysis 1.1 仕様によってサポートされています。<br /><br /> -   [Statement 要素&#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)|以下のコマンドが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってサポートされています。<br /><br /> -   [Alter 要素&#40;XMLA&#41;](xml-elements-commands/alter-element-xmla.md)<br />-   [バックアップ要素&#40;XMLA&#41;](xml-elements-commands/backup-element-xmla.md)<br />-   [要素をバッチ&#40;XMLA&#41;](xml-elements-commands/batch-element-xmla.md)<br />-   [BeginTransaction 要素&#40;XMLA&#41;](xml-elements-commands/begintransaction-element-xmla.md)<br />-   [Cancel 要素&#40;XMLA&#41;](xml-elements-commands/cancel-element-xmla.md)<br />-   [ClearCache 要素&#40;XMLA&#41;](xml-elements-commands/clearcache-element-xmla.md)<br />-   [CommitTransaction 要素&#40;XMLA&#41;](xml-elements-commands/committransaction-element-xmla.md)<br />-   [要素作成&#40;XMLA&#41;](xml-elements-commands/create-element-xmla.md)<br />-   [要素の削除&#40;XMLA&#41;](xml-elements-commands/delete-element-xmla.md)<br />-   [DesignAggregations 要素&#40;XMLA&#41;](xml-elements-commands/designaggregations-element-xmla.md)<br />-   [Drop 要素&#40;XMLA&#41;](xml-elements-commands/drop-element-xmla.md)<br />-   [要素を挿入&#40;XMLA&#41;](xml-elements-commands/insert-element-xmla.md)<br />-   [要素をロック&#40;XMLA&#41;](xml-elements-commands/lock-element-xmla.md)<br />-   [MergePartitions 要素&#40;XMLA&#41;](xml-elements-commands/mergepartitions-element-xmla.md)<br />-   [NotifyTableChange 要素&#40;XMLA&#41;](xml-elements-commands/notifytablechange-element-xmla.md)<br />-   [要素を処理&#40;XMLA&#41;](xml-elements-commands/process-element-xmla.md)<br />-   [Restore 要素&#40;XMLA&#41;](xml-elements-commands/restore-element-xmla.md)<br />-   [RollbackTransaction 要素&#40;XMLA&#41;](xml-elements-commands/rollbacktransaction-element-xmla.md)<br />-SetPasswordEncryptionKey 要素<br />-   [Statement 要素&#40;XMLA&#41;](xml-elements-commands/statement-element-xmla.md)<br />-   [Subscribe 要素&#40;XMLA&#41;](xml-elements-commands/subscribe-element-xmla.md)<br />-   [Synchronize 要素&#40;XMLA&#41;](xml-elements-commands/synchronize-element-xmla.md)<br />-   [要素のロック解除&#40;XMLA&#41;](xml-elements-commands/unlock-element-xmla.md)<br />-   [Update 要素&#40;XMLA&#41;](xml-elements-commands/update-element-xmla.md)<br />-   [UpdateCells 要素&#40;XMLA&#41;](xml-elements-commands/updatecells-element-xmla.md)|  
|表形式の行セットでの列エラー|XML for Analysis 1.1 仕様にはリストされていません。|[エラー](xml-elements-properties/error-element-xmla.md)要素によって使用されます[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に含まれる列要素のエラーを報告する、[行](xml-elements-properties/error-element-xmla.md)要素。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis &#40;XMLA&#41;リファレンス](xml-for-analysis-xmla-reference.md)  
  
  
