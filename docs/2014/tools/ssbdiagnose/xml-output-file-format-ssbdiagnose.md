---
title: XML 出力ファイルの形式 (ssbdiagnose) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML output file format [ssbdiagnose]
- ssbdiagnose
ms.assetid: 3ceb991b-6f15-4504-8828-de5adf448bc5
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 9b8f29b17e54c0abf406ee30ad542d960d4556ef
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174387"
---
# <a name="xml-output-file-format-ssbdiagnose"></a>XML 出力ファイルの形式 (ssbdiagnose)
  **ssbdiagnose** ユーティリティは、**-XML** スイッチを指定して実行した場合、その出力を XML ファイルとして配布します。 XML 出力ファイルでは、ヘッダー情報と、分析された [!INCLUDE[ssSB](../../includes/sssb-md.md)] の構成またはメッセージ交換で検出されたエラーが示されます。 ファイルに示されたエラーを分析して報告するためのアプリケーションを作成することができます。 また、XML ファイルを XML Notepad などの一般的な XML エディターで表示することもできます。  
  
 **ssbdiangose** の出力ファイルには、2 種類の子を持つ DiagnosticInformation ルート要素が含まれます。  
  
-   ヘッダー情報を含む Banner 要素。  
  
-   **ssbdiagnose**によって報告される各問題を示す Issue 要素。  
  
## <a name="diagnosticinformation-root-element"></a>DiagnosticInformation ルート要素 (ssbdiagnose)  
  
-   [DiagnosticInformation 要素&#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)  
  
## <a name="banner-element"></a>Banner 要素  
  
-   [Banner 要素&#40;ssbdiagnose&#41;](banner-element-ssbdiagnose.md)  
  
## <a name="issue-element"></a>Issue 要素  
  
-   [Issue 要素&#40;ssbdiagnose&#41;](issue-element-ssbdiagnose.md)  
  
## <a name="see-also"></a>参照  
 [ssbdiagnose ユーティリティ &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  