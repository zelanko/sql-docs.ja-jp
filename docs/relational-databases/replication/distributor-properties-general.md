---
title: '[ディストリビューターのプロパティ]、[全般] | Microsoft Docs'
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.distproperties.general.f1
helpviewer_keywords:
- Distributor Properties dialog box
ms.assetid: ab4120ec-e524-4c0c-8b48-f2f40adb1a3b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 73f610471c4142e6a0c87f4f4ece5eacc28426de
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621680"
---
# <a name="distributor-properties-general"></a>[ディストリビューターのプロパティ]、[全般]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[ディストリビューターのプロパティ]** ダイアログ ボックスの **[全般]** ページを使用すると、ディストリビューション データベースの追加と削除や、ディストリビューション データベースのプロパティの設定を行うことができます。  
  
 ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションのトランザクションが格納されます。 多くの場合、ディストリビューション データベースは 1 つで十分です。 ただし、複数のパブリッシャーが 1 つのディストリビューターを使用する場合、各パブリッシャーにディストリビューション データベースを作成することを検討してください。 これによって、各ディストリビューション データベースを経由するデータ フローが区別されます。  
  
## <a name="options"></a>[変数]  
 **データベース**  
 **[データベース]** プロパティ グリッドには、ディストリビューターのディストリビューション データベースの名前と保有期間のプロパティが表示されます。 **[トランザクションの保有期間]** は、トランザクションがトランザクション レプリケーションに格納される期間です (トランザクションの保有期間は、ディストリビューションの保有期間でもあります)。 **[履歴の保有期間]** は、履歴メタデータがすべての種類のレプリケーションに格納される期間です。 ディストリビューション保有期間の詳細については、「[Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」 (サブスクリプションの有効期限と非アクティブ化) を参照してください。  
  
 **[ディストリビューション データベースのプロパティ]** ダイアログ ボックスを表示するには、 **[データベース]** プロパティ グリッドのプロパティ ボタン ( **[...]** ) をクリックします。  
  
 **[新規作成]**  
 新しいディストリビューション データベースを作成します。  
  
 **削除**  
 **[データベース]** プロパティ グリッドで既存のディストリビューション データベースを選択し、 **[削除]** をクリックしてデータベースを削除します。 ディストリビューターは少なくとも 1 つのディストリビューション データベースを持つ必要があるため、データベースが 1 つだけの場合はディストリビューション データベースを削除することはできません。 すべてのディストリビューション データベースを削除するには、コンピューターでディストリビューションを無効にする必要があります。 詳細については、「[Disable Publishing and Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)」 (パブリッシングおよびディストリビューションの無効化) を参照してください。  
  
 **[プロファイルの既定値]**  
 **[エージェント プロファイル]** ダイアログ ボックスのレプリケーション エージェント プロファイルにアクセスします。 プロファイルの詳細については、「 [Replication Agent Profiles](../../relational-databases/replication/agents/replication-agent-profiles.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
