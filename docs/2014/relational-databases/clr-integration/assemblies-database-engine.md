---
title: アセンブリ (データベースエンジン) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- assemblies [CLR integration]
- assemblies [CLR integration], about assemblies
- managed code [SQL Server], assemblies
ms.assetid: 4b146437-3061-47f6-9e8c-26eeea10b54e
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4830a677125cb03e2c53ed78065d94d5265d4a83
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62920780"
---
# <a name="assemblies-database-engine"></a>アセンブリ (データベース エンジン)
  このセクションのトピックでは、アセンブリの理解、設計、および実装に役立つ情報について説明します。  
  
 アセンブリは、関数、ストアドプロシージャ、トリガー [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、ユーザー定義集計、およびユーザー定義型を配置するために、のインスタンスで使用される DLL ファイルです。で[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] [!INCLUDE[tsql](../../../includes/tsql-md.md)]はなく、共通言語ランタイム (CLR) によってホストされるマネージコード言語のいずれかで記述されます。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のアセンブリは、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 共通言語ランタイムで作成されたマネージド アプリケーション モジュール (.dll ファイル) を参照するオブジェクトです。 アセンブリには、クラス メタデータとマネージド コードが含まれています。 SQL Server のインスタンスにアセンブリをアップロードすることが、次のいずれかのデータベース オブジェクトを作成するための最初の手順になります。  
  
-   CLR 関数。 詳細については、「 [CLR 関数の作成](../user-defined-functions/create-clr-functions.md)」を参照してください。  
  
-   CLR ストアド プロシージャ。 詳細については、「 [CLR ストアドプロシージャ](../../database-engine/dev-guide/clr-stored-procedures.md)」を参照してください。  
  
-   CLR トリガー。 詳細については、「 [CLR トリガーの作成](../triggers/create-clr-triggers.md)」を参照してください。  
  
-   ユーザー定義集計関数。 詳細については、「[ユーザー定義集計を作成する](../user-defined-functions/create-user-defined-aggregates.md)」を参照してください。  
  
-   ユーザー定義型。 詳細については、「[ユーザー定義型の使用](../native-client/features/using-user-defined-types.md)」を参照してください。  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、アセンブリによって次の関数が実行されます。  
  
-   上記の 1 つ以上の CLR データベース オブジェクトの機能を実行するマネージド コードを含む関数。  
  
-   アセンブリのバージョン番号とカルチャ、アセンブリのクラスの一覧を一意に識別する省略可能なパブリック キー、アセンブリで定義されたメソッド、アセンブリのプロセッサ アーキテクチャなどのメタデータを含む関数。  
  
-   コード アクセス権を管理することにより、マネージド コードがリソース外部にアクセスできる程度を管理する関数。  
  
-   アセンブリによって参照される他のアセンブリの依存関係に関するメタデータを含む関数。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|[説明]|  
|-----------|-----------------|  
|[アセンブリのデザイン](assemblies-designing.md)|アセンブリを作成する前の注意事項について説明します。 これには、アセンブリのパッケージ化、コード アクセス権、その他の制限事項などがあります。|  
|[アセンブリの実装](assemblies-implementing.md)|アセンブリを作成または削除する方法、アセンブリを変更するタイミングとその方法、およびアセンブリに関するメタデータの取得方法について説明します。|  
|[アセンブリについての情報の取得](assemblies-getting-information.md)|アセンブリに関するメタデータに対してクエリを実行可能なカタログ ビューや関数を一覧します。|  
  
## <a name="see-also"></a>参照  
 [共通言語ランタイム &#40;CLR&#41; 統合プログラミングの概念](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
