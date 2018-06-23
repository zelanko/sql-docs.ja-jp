---
title: データ処理拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
caps.latest.revision: 33
author: douglaslM
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 0ea72edfcea9935b858631a639ec51f67a3feeac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173882"
---
# <a name="removing-a-data-processing-extension"></a>データ処理拡張機能の削除
  データ処理拡張機能を削除する場合は、データ処理拡張機能の **Extension** 要素を構成ファイルから削除するだけです。 レポート サーバーに加えてレポート デザイナーにもエントリを作成した場合は、RSReportServer.config ファイルと RSReportDesigner.config ファイルの両方から **Extension** 要素を削除します。 構成情報を削除すると、そのコンポーネントではデータ処理拡張機能を使用できなくなります。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../reporting-services-extensions.md)   
 [データ処理拡張機能の実装](implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  