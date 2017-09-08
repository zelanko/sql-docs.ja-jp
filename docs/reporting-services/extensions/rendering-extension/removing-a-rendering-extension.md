---
title: "表示拡張機能の削除 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/18/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
caps.latest.revision: 38
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: ea37cf7ac15504a00aeb0f1379e9d48a71231e1c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="removing-a-rendering-extension"></a>表示拡張機能を削除します。
  削除する、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]表示拡張機能を削除するだけ、**拡張子**要素にある rsreportserver.config ファイルから表示拡張機能を**%ProgramFiles%\Microsoft SQL server \msrs10_50.\< 。インスタンス名 > \reporting**フォルダーです。 レポート デザイナーとレポート サーバーのエントリを作成した場合は、削除、**拡張子**から要素を[RSReportDesigner Configuration File](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md)もします。 構成情報を削除した後は、表示拡張機能をコンポーネントに使用できません。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [表示拡張機能を実装します。](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [表示拡張機能の概要](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [IRenderingExtension インターフェイスの実装](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [セキュリティ拡張機能に関する考慮事項](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [表示拡張機能の配置](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
