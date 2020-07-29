---
title: 登録済みサーバーまたはサーバー グループの名前の変更
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 10e1546b-9edb-400c-8676-2ea1192d6134
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 08/02/2016
ms.openlocfilehash: 32f59e2db98280a7d096e0f1f7d1a90895db010b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86001785"
---
# <a name="change-the-name-of-registered-server-or-registered-server-group"></a>登録済みサーバーまたは登録済みサーバー グループの名前の変更

[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用して、登録済みサーバーまたは登録済みサーバー グループの名前を変更する方法について説明します。 この名前はいつでも変更できます。 [登録済みサーバー] でサーバーの名前を変更すると、名前の表示のみが変更されます。 別のサーバーに接続するには、登録済みサーバーの接続プロパティを編集する必要があります。  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用

メニューから **[表示]\\[登録済みサーバー]** を選択し、 **[登録済みサーバー]** ペインを開きます。

### <a name="to-change-the-name-of-a-server"></a>サーバーの名前を変更するには

1. **[登録済みサーバー]** の **[データベース エンジン]** 、 **[ローカル サーバー グループ]** の順に展開します。  

2. サーバーを右クリックして **[プロパティ]** を選択し、 **[サーバー登録プロパティの編集]** ダイアログ ボックスを開きます。

3. **[登録済みサーバーの名前]** テキスト ボックスにサーバーの新しい登録名を入力し、 **[保存]** をクリックします。  

### <a name="to-change-the-name-of-a-server-group"></a>サーバー グループの名前を変更するには  

1. **[登録済みサーバー]** の **[データベース エンジン]** 、 **[ローカル サーバー グループ]** の順に展開します。  

2. サーバー グループを右クリックし、 **[プロパティ]** を選択して **[サーバー グループ プロパティの編集]** ダイアログ ボックスを開きます。 

3. **[グループ名]** テキスト ボックスにサーバー グループの新しい名前を入力し、 **[保存]** をクリックします。  

## <a name="see-also"></a>参照

[サーバーの登録の変更 &#40;SQL Server Management Studio&#41;](../../tools/sql-server-management-studio/change-a-server-s-registration-sql-server-management-studio.md)