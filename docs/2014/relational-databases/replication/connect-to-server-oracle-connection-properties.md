---
title: '[サーバーへの接続] (Oracle)、[接続プロパティ] | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.oracleconnection.connectionprops.f1
helpviewer_keywords:
- Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 479b0d562ffb78bc0003ca320eea0a85ab172430
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721694"
---
# <a name="connect-to-server-oracle-connection-properties"></a>[サーバーへの接続] (Oracle)、[接続プロパティ]
  
  **[サーバーへの接続]** ダイアログ ボックスの **[接続プロパティ]** タブを使用すると、 **[ゲートウェイ]** または **[完全]** のパブリッシュ オプションを指定できます。 パブリッシャーを識別した後は、パブリッシャーをいったん削除して再構成しない限り、このオプションは変更できません。 詳細については、「[Configure an Oracle Publisher](non-sql/configure-an-oracle-publisher.md)」(Oracle パブリッシャーの構成) をご覧ください。  
  
## <a name="options"></a>オプション  
 **パブリッシャーの種類**  
 
  **[ゲートウェイ]** または **[完全]** を選択します。 
  **[完全]** オプションを選択した場合は、Oracle パブリッシング用にサポートされる完全な機能セットがスナップショットおよびトランザクション パブリケーションに提供されます。 
  **[ゲートウェイ]** オプションを選択した場合は、レプリケーションがシステム間のゲートウェイとして動作する場合のパフォーマンスを向上させるために、特定のデザインが最適化されます。 複数のトランザクション パブリケーションに同じテーブルをパブリッシュする場合は、 **[ゲートウェイ]** オプションは使用できません。 
  **[ゲートウェイ]** オプションを選択した場合、1 つのテーブルは、最大で 1 つのトランザクション パブリケーションおよび任意の数のスナップショット パブリケーションに含めることができます。  
  
 **タイムアウト**  
 タイムアウトエラーが発生[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]する前にディストリビューターが Oracle パブリッシャーへの接続を試行する時間を指定します。  
  
## <a name="see-also"></a>参照  
 [Oracle パブリッシングの用語集](non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Oracle パブリッシャーのパフォーマンスチューニング](non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
