---
title: Oracle への接続 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- connOra
ms.assetid: 711ac7ff-5d3d-4533-80ca-d1fecdb3048f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9be5e4b3652dec337583123e0232ce9b1442af73
ms.sourcegitcommit: c8e1553ff3fdf295e8dc6ce30d1c454d6fde8088
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924000"
---
# <a name="connect-to-oracle"></a>Oracle への接続

[!INCLUDE[sqlserver-ssis](../../includes/applies-to-version/sqlserver-ssis.md)]


  CDC インスタンスに使用するテーブルを初めて追加または編集するとき、Oracle データベースへの接続を要求されることがあります。 キャプチャするテーブルのスキーマにアクセスできる Oracle ユーザーの資格情報を入力する必要があります。 このダイアログ ボックスでは次の情報を入力します。  
  
 **認証**  
  
 次のいずれかを選択してください。  
  
-   **[Windows 認証]** : 現在の Windows ドメイン資格情報を使用する場合に選択します。 このオプションは、Oracle データベースが Windows 認証と連動するように構成されている場合にのみ使用できます。  
  
-   **[Oracle 認証]** : このオプションを選択する場合、接続先の Oracle データベースのユーザーの **[ユーザー名]** と **[パスワード]** を入力する必要があります。  
  
## <a name="see-also"></a>参照  
 [CDC へのテーブルの追加](../../integration-services/change-data-capture/add-tables-to-a-cdc-instance.md)  
  
  
