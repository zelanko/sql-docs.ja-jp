---
title: XML 出力ファイルの形式 (ssbdiagnose) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssbdiagnose
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 13
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 11c9dbc6f279782a0083a12b0ce304f5959e58ad
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="xml-output-file-format-ssbdiagnose"></a>XML 出力ファイルの形式 (ssbdiagnose)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **ssbdiagnose** ユーティリティは、**-XML** スイッチを指定して実行した場合、その出力を XML ファイルとして配布します。 XML 出力ファイルでは、ヘッダー情報と、分析された [!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成またはメッセージ交換で検出されたエラーが示されます。 ファイルに示されたエラーを分析して報告するためのアプリケーションを作成することができます。 また、XML ファイルを XML Notepad などの一般的な XML エディターで表示することもできます。  
  
 **ssbdiangose** の出力ファイルには、2 種類の子を持つ DiagnosticInformation ルート要素が含まれます。  
  
-   ヘッダー情報を含む Banner 要素。  
  
-   **ssbdiagnose**によって報告される各問題を示す Issue 要素。  
  
## <a name="diagnosticinformation-root-element"></a>DiagnosticInformation ルート要素 (ssbdiagnose)  
  
-   [DiagnosticInformation 要素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Banner 要素  
  
-   [Banner 要素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Issue 要素  
  
-   [Issue 要素 &#40;ssbdiagnose&#41;](../../tools/ssbdiagnose/issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>参照  
 [ssbdiagnose ユーティリティ &#40;Service Broker&#41;](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
  
