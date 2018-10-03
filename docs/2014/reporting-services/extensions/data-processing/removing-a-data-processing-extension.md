---
title: データ処理拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 7a1ad001df3353d4f114ec5ef38af2a7fdc9f142
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200052"
---
# <a name="removing-a-data-processing-extension"></a>データ処理拡張機能の削除
  データ処理拡張機能を削除する場合は、データ処理拡張機能の **Extension** 要素を構成ファイルから削除するだけです。 レポート サーバーに加えてレポート デザイナーにもエントリを作成した場合は、RSReportServer.config ファイルと RSReportDesigner.config ファイルの両方から **Extension** 要素を削除します。 構成情報を削除すると、そのコンポーネントではデータ処理拡張機能を使用できなくなります。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../reporting-services-extensions.md)   
 [データ処理拡張機能の実装](implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  
