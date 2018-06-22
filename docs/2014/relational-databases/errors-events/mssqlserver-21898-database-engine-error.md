---
title: MSSQLSERVER_21898 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21898 (Database Engine error)
ms.assetid: 02405b21-3d4e-4c2d-b4b3-d7b1ec05edb4
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2a33000c20c7c8c1399f8f6db653d60841bb7de2
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36073496"
---
# <a name="mssqlserver21898"></a>MSSQLSERVER_21898
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21898|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21898|  
|メッセージ テキスト|パブリッシャー '%s' は、ディストリビューション データベース '%s' を使用しますが、パブリッシング データベース '%s' をホストするために必要な '%s' を使用していません。 ディストリビューター '%s' で `sp_changedistpublisher` を実行して、パブリッシャーで使用されるディストリビューション データベースを '%s' に変更してください。|  
  
## <a name="explanation"></a>説明  
 `sp_validate_redirected_publisher` 新しいパブリッシャーによって使用されるディストリビューション データベースが元のパブリッシャーによって使用されるディストリビューション データベースと同じであることを確認する、ローカル ディストリビューターで msdb.dbo.MSdistpublishers を照会します。 このエラーは、これらのデータベースが異なり、パブリッシャーがパブリッシャー データベースに不適切なホストになる場合に発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 ストアド プロシージャ `sp_changedistpublisher` を実行し、新しいパブリッシャーのディストリビューション データベースを元のパブリッシャーによって使用されるデータベースに変更します。  
  
> [!NOTE]  
>  `sp_changedistpublisher` を実行すると、パブリッシャーのディストリビューターで `sp_adddistpublisher` を実行したときに間違ったディストリビューション データベースを入力した場合の問題が解決されます。 ただし、識別されたディストリビューション データベースを使用する別のパブリッシング データベースからの既存のパブリケーションがリモート パブリッシャーにある場合、この変更は適切ではありません。 指定されたディストリビューション データベースを使用するレプリケーションは、新しいパブリッシャーが適切なホストとして機能するために、体系的に削除してから元のパブリッシャーのディストリビューション データベースを使用して再確立する必要があります。  
  
  