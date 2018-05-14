---
title: '[警告のプロパティ] - [新しい警告] ([応答] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.ag.alert.response.f1
ms.assetid: 72daf008-f9ea-4077-b217-5048e7759d3e
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 3b6fc99f0eb6266979e122d82cbc2d2ce2578498
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="alert-properties---new-alert-response-page"></a>[警告のプロパティ] - [新しい警告] ([応答] ページ)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database マネージ インスタンス](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)では現在、すべてではありませんがほとんどの SQL Server エージェントの機能がサポートされています。 詳細については、「[Azure SQL Database マネージ インスタンスと SQL Server の T-SQL の相違点](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)」を参照してください。

このページを使用すると、実行するジョブや、オペレーターの一覧を取得するジョブを指定できます。この一覧のオペレーターは、 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] エージェントの警告に関する通知を受け取ります。  

## <a name="options"></a>および  
**[ジョブの実行]**  
**[ジョブ一覧]**、 **[新しいジョブ]** 、および **[ジョブの表示]** の各オプションを有効にします。  
  
**[新しいジョブ]**  
**[新しいジョブ]** ダイアログ ボックスを開きます。 **[ジョブの実行]** が選択されていない場合、このボタンは使用できません。  
  
**[ジョブの表示]**  
選択されているジョブを表示または変更します。 **[ジョブの実行]** が選択されていない場合、このオプションは使用できません。  
  
**[オペレーターに通知する]**  
オペレーターを追加、削除、または変更できるようにするためのコントロールを有効にします。  
  
**[オペレーター一覧]**  
警告の発生時に通知するオペレーターの一覧を表示します。 通知方法を指定するには、オペレーター名の後に表示されている **[電子メール]**、 **[ポケットベル]**、または **[Net Send]** チェック ボックスをオンにします。 **[オペレーターに通知する]** が選択されていない場合、このオプションは使用できません。  
  
**[電子メール]**  
電子メールを使用してオペレーターに通知します。  
  
**[ポケットベル]**  
ポケットベルの電子メール アドレスを使用してオペレーターに通知します。  
  
**[Net Send]**  
**net send** を使用してオペレーターに通知します。  
  
**[新しいオペレーター]**  
**[新しいオペレーター]** ダイアログ ボックスを表示します。このダイアログ ボックスを使用して、新しいオペレーターを作成できます。  
  
**[オペレーターの表示]**  
現在選択されているオペレーターの **[プロパティ]** ダイアログ ボックスを表示します。 **[オペレーターのプロパティ]** ダイアログ ボックスで、オペレーターのプロパティを表示および変更できます。  
  
## <a name="see-also"></a>参照  
[警告](../../ssms/agent/alerts.md)  
[Create an Alert Using Severity Level](../../ssms/agent/create-an-alert-using-severity-level.md)  
[警告](../../ssms/agent/alerts.md)  
[Edit an Alert](../../ssms/agent/edit-an-alert.md)  
[Delete an Alert](../../ssms/agent/delete-an-alert.md)  
  
