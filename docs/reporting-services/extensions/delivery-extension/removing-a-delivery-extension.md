---
title: 配信拡張機能の削除 | Microsoft Docs
ms.date: 03/06/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: markingmyname
ms.author: maghan
ms.openlocfilehash: daebad069ec1d9791ceab58af1d25f03524c82cc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704910"
---
# <a name="removing-a-delivery-extension"></a>配信拡張機能の削除
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を削除する場合は、配信拡張機能の **Extension** 要素を構成ファイルから削除するだけです。 構成情報を削除した後は、配信拡張機能をレポート サーバーに使用できません。  
  
 配信拡張機能の対応する **Extension** 要素を構成ファイルから削除すると、この要素はレポート サーバーに登録されなくなります。 レポート サーバーは、配信拡張機能の一覧からエントリを削除し、配信拡張機能を使用するサブスクリプションをすべて非アクティブにします。 配信拡張機能が削除されていると、ユーザーは配信拡張機能を通知のメソッドとして選択できなくなります。  
  
## <a name="see-also"></a>参照  
 [配信拡張機能の実装](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
