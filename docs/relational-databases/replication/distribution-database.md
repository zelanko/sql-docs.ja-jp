---
title: ディストリビューション データベース | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configuredistributionwizard.distributiondatabase.f1
ms.assetid: 5b42a083-7a11-41d8-9e3f-320c7c907237
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 9f86ef648812c553a2445afac6a50f03824e8e72
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "76284509"
---
# <a name="distribution-database"></a>ディストリビューション データベース
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  ディストリビューション データベースには、すべての種類のレプリケーションのメタデータと履歴データ、およびトランザクション レプリケーションのトランザクションが格納されます。  
  
 多くの場合、ディストリビューション データベースは 1 つで十分です。 ただし、複数のパブリッシャーが 1 つのディストリビューターを使用する場合は、各パブリッシャーにディストリビューション データベースを作成することを検討してください。 これによって、各ディストリビューション データベースを経由するデータ フローが区別されます。 ディストリビューターに 1 つのディストリビューション データベースを指定するには、ディストリビューション構成ウィザードを使用します。 必要に応じて、 **[ディストリビューターのプロパティ]** ダイアログ ボックスで追加のディストリビューション データベースを指定できます。  
  
## <a name="options"></a>オプション  
 **[ディストリビューション データベース名]**  
 ディストリビューション データベースに付ける名前を入力します。 ディストリビューション データベースの既定の名前は "distribution" です。 名前を付ける場合は、128 文字以内で、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意であり、識別子のルールに準拠している名前にする必要があります。 詳細については、「[データベース識別子](../../relational-databases/databases/database-identifiers.md)」を参照してください。  
  
 **[ディストリビューション データベース ファイルのフォルダー]** と **[ディストリビューション データベース ログ ファイルのフォルダー]**  
 ディストリビューション データベース ファイルとログ ファイルのパスを入力します。 パスは、ディストリビューターにとってローカルなディスクを参照し、ローカル ドライブ名とコロン (C: など) で始まる必要があります。 マップされたドライブ名およびネットワーク パスは無効です。  
  
> [!NOTE]  
>  ディストリビューション データベース ログをディストリビューション データベースとは別のディスク ドライブに置くようにすると、トランザクションの書き込みに要する時間が短縮され、レプリケーションのパフォーマンスが向上します。  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)   
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)  
  
  
