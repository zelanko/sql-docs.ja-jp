---
title: Change Data Capture Service for Oracle by Attunity のシステム アーキテクチャ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1db6c737-3c60-4066-a0a3-3611e1c83e4e
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e04a6a174143d2da6d85ae27dd84ecf516f533fa
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52756882"
---
# <a name="change-data-capture-service-for-oracle-by-attunity-system-architecture"></a>Change Data Capture Service for Oracle by Attunity のシステム アーキテクチャ
  CDC Service for Oracle は、1 つ以上のソース Oracle データベースの選択したテーブルに加えられた変更を、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスにある [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC データベースにキャプチャします。 次の図に、CDC Service for Oracle を構成するコンポーネントを示します。  
  
 ![サービスのアーキテクチャ](../media/service-architecture.gif "サービスのアーキテクチャ")  
  
 この図は、使用される 4 つのプラットフォームを示しています。 多くの場合、これらのプラットフォームは重複させることができますが、この図では標準的なユース ケースを示しています。 たとえば、Oracle データベースと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースのそれぞれを独立したコンピューターで実行し、Oracle CDC Service プラットフォームまたは CDC Service の設計元であるプラットフォームと共有しないようにするのが適切です。 この図に示すプラットフォームは次のとおりです。  
  
-   Oracle CDC Service:任意のサポートされている Windows コンピューター、Oracle CDC Service をインストールして実行する場所を指定できます。 このプラットフォームは、Microsoft フェールオーバー クラスターのクラスター ノードを表す場合もあります (高可用性構成については、このドキュメントで後ほど説明します)。  
  
-   Oracle データベース:サポートされているバージョンの Oracle データベースが実行されている任意のコンピューターを指定できます。 これには、Windows、Linux、またはインストールされた Oracle データベースのバージョンがサポートする他の任意のオペレーティング システムを実行するコンピューターが含まれます。 このプラットフォームは図で複数示されています。これは、単一の Oracle CDC Service で複数のソース Oracle データベースの変更をキャプチャできるためです。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:任意のコンピューターは、これでターゲット[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース (のサポートされている SKU [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]) を実行します。 Oracle CDC Service は、変更テーブルおよびサービス構成を格納する 1 つの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ターゲットをサポートします。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プラットフォームは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] のクラスター化されたインスタンスまたは [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] の **AlwaysOn** 機能を使用してミラー化されたインスタンスを表す場合もあります。  
  
-   Oracle CDC デザイナー:ソース Oracle データベースとターゲットがアクセスできる任意のサポートされている Windows コンピューターは、この[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース。  
  
 次の表に、上記の 4 つのプラットフォームで実行されるコンポーネントを示します。  
  
|コンポーネント/説明|コンポーネントの構成要素|  
|----------------------------|----------------------------|  
|Oracle CDC Service:これは、変更データ キャプチャの操作が行われる Windows サービスです。|Oracle CDC インスタンス:変更 (ソース Oracle データベースごとに 1 つの Oracle CDC インスタンスがある)、1 つのソース Oracle データベースのデータのキャプチャ操作を処理する Oracle CDC Service のサブプロセスです。<br /><br /> Oracle ログ リーダー:Oracle クライアントを使用して Oracle トランザクション ログを読み取ります。<br /><br /> Oracle クライアント:Oracle との通信に使用される Oracle Instant Client です。 これは、Oracle CDC Service をインストールする前に Oracle から入手してインストールする必要がある必須ソフトウェアです。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 変更ライター:これにキャプチャされた Oracle テーブルにコミットされた変更を書き込みます[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]テーブルを変更します。 また、このコンポーネントはキャプチャ状態を対象の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース内に維持します。<br /><br /> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ODBC クライアント:マイクロソフトのネイティブ クライアントの[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]します。 これは、Oracle CDC Service をインストールする前にマイクロソフトから入手してインストールする必要がある必須コンポーネントです。|  
|Oracle CDC Service 構成:これは、Windows サービスを作成し、その構成を設定する Microsoft 管理コンソール スナップインです。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント:.NET framework version 4 に付属する SQL ADO.NET クライアント。|  
|Oracle データベース:元のソース Oracle データベース テーブルの選択の変更がキャプチャされます。|ログ マイナー:Oracle トランザクション ログの読み取り、Oracle コンポーネントです。<br /><br /> トランザクション ログ:オンラインまたはアーカイブされた Oracle 再実行ログを使って oracle データベースもロールバックになっていることを確実には、トランザクションをバックアップし、(この場合は、Oracle のデータベースは、アーカイブ ログ モードで動作する必要があります) での障害から回復します。|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス:A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC データベースがホストされているインスタンス。 これはクラスター化された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンス (フェールオーバー クラスター) またはミラー化されたデータベース (AlwaysOn) です。|MSXDBCDC データベース:データベースでこの CDC サービスについて[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンスが保持されます。 また、各 CDC Service によって処理される Oracle CDC インスタンスの情報も保持されます。 このデータベースは、CDC Service 作成プロセスの一環として作成されます。<br /><br /> CDC データベース: いずれかのソース Oracle データベースに加えられた変更を格納する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースです。 CDC データベースは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC に対して有効になります。そのため、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] CDC のテーブルおよび機能を含み、Oracle からの変更を簡単に処理できます。|  
|Oracle CDC デザイナー:ときに役立つ Microsoft 管理コンソール スナップインは、Oracle CDC インスタンスを作成します。 このスナップインを使用して、キャプチャするテーブルおよび列を選択し、Oracle 接続情報を提供し、CDC インスタンスのライフ サイクルを管理します。|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] クライアント:.NET framework version 4 に付属する SQL ADO.NET クライアント。<br /><br /> Oracle クライアント:Oracle との通信に使用される Oracle Instant Client です。 これは、Oracle CDC Service をインストールする前に Oracle から入手してインストールする必要がある必須コンポーネントです。|  
  
 Oracle CDC Service とその子である Oracle CDC インスタンスは、ソース Oracle データベースおよびクライアントである対象の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスのみと通信できます。 ネットワーク プロトコルやその他のプロトコルの積極的なリッスンは行いません。 Oracle CDC Service は、CDC データベースを監視して構成の変更を検出し、更新された構成に基づいて操作を更新します。  
  
  
