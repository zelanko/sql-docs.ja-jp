---
title: "COM ベースのカスタム競合回避モジュール | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM-based resolvers [SQL Server replication]
- custom resolvers [SQL Server replication]
ms.assetid: 94195797-ad7a-4962-a8e3-b259cd13aa38
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 88ccc09da5973beffdfa8b2595b1354c95b4cbb1
ms.lasthandoff: 04/11/2017

---
# <a name="advanced-merge-replication-conflict---com-based-custom-resolvers"></a>マージ レプリケーションの競合の詳細 - COM ベースのカスタム競合回避モジュール
  カスタム競合回避モジュールを使用すると、既定の解決メカニズムより高い柔軟性が得られ、レプリケートされたデータを使用するアプリケーションに必要なビジネス ロジックを実装できます。 COM ベースのカスタム競合回避モジュールは、 **ICustomResolver** COM インターフェイス、メソッドとプロパティ、および競合解決専用に設計されたその他のインターフェイスとデータ型定義を実装するダイナミック リンク ライブラリ (DLL) です。  
  
> [!NOTE]  
>  可能であれば、COM ベースのカスタム競合回避モジュールではなくビジネス ロジック ハンドラーを使用することをお勧めします。 ビジネス ロジック ハンドラーの詳細については、「[Execute Business Logic During Merge Synchronization](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)」 (マージ同期中のビジネス ロジックの実行) を参照してください。  
  
 カスタム COM 競合回避モジュールを作成する場合は、replrec.dll に含まれているタイプ ライブラリを使用できます。このライブラリは、既定では [!INCLUDE[ssInstallPath](../../../includes/ssinstallpath-md.md)]COM にインストールされます。  
  
 カスタム COM 競合解決モジュールを記述する前に、以下のことを決定する必要があります。  
  
-   更新、挿入、削除など、解決する必要がある行の変更の種類、およびマージ変更のアップロード、ダウンロード、またはその両方で競合回避モジュールを呼び出すかどうか。 1 種類の変更、すべての変更、または各変更の組み合わせを指定できます。 既定のマージ競合回避モジュールでは、カスタム競合回避モジュールで対応しなかった競合が処理されます。  
  
-   競合の解決時に列レベルの追跡を使用するかどうか。 列レベルの追跡が有効になっている場合、競合が発生した列のデータに対してのみ競合のフラグが付けられ、それ以外の場合、データはマージされます。 しかし、競合の解決方法は行レベルの追跡の場合と同じです。競合で優先されるデータによって行全体が上書きされます。ただし、データは、パブリッシャー、サブスクライバー、またはそれ以外で変更された値が混合されている場合があります。 詳細については、「 [Detect and Resolve Merge Replication Conflicts](../../../relational-databases/replication/merge/advanced-merge-replication-resolve-merge-replication-conflicts.md)」を参照してください。  
  
 COM ベースのカスタム競合回避モジュールを実装するには、「 [Implement a Custom Conflict Resolver for a Merge Article](../../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)」を参照してください。  
  
 カスタム競合回避モジュールは、パブリケーション全体ではなくアーティクルに対して指定されます。 複数のアーティクルで同じ競合回避モジュールを使用できますが、カスタム競合回避モジュールのロジックは特定のテーブル専用であるのが一般的です。 競合回避モジュールを作成した後に、アーティクルで使用されているテーブルが変更されると (競合解決に使用している列の名前が変更された場合など)、カスタム競合回避モジュールを変更して再コンパイルすることが必要な場合があります。  
  
 カスタム競合回避モジュールを指定するには、「 [Specify a Merge Article Resolver](../../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [Microsoft COM ベースの競合回避モジュール](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)  
  
  
