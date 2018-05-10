---
title: データ処理拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.component: extensions
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
caps.latest.revision: 34
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 01f260e3bb3be11ec878c951470e420fe6156647
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="removing-a-data-processing-extension"></a>データ処理拡張機能の削除
  データ処理拡張機能を削除する場合は、データ処理拡張機能の **Extension** 要素を構成ファイルから削除するだけです。 レポート サーバーに加えてレポート デザイナーにもエントリを作成した場合は、RSReportServer.config ファイルと RSReportDesigner.config ファイルの両方から **Extension** 要素を削除します。 構成情報を削除すると、そのコンポーネントではデータ処理拡張機能を使用できなくなります。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [データ処理拡張機能の実装](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
