---
title: データベース ミラーリング監視サーバー | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], about witness
- witness [SQL Server]
- database mirroring [SQL Server], witness
ms.assetid: 05606de8-90c3-451a-938d-1ed34211dad7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 682a3692414f89beb0c5e0f0204bc1a69b532e64
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62807631"
---
# <a name="database-mirroring-witness"></a>データベース ミラーリング監視サーバー
  自動フェールオーバーをサポートするには、データベースミラーリングセッションを高い安全性モードで構成する必要があります。また、ミラーリング*監視*サーバーと呼ばれる3つ目のサーバーインスタンスも必要です。 ミラーリング監視サーバーは、必要に応じて配置できる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスです。ミラーリング監視サーバーを使用することにより、高い安全性モードのセッションのミラー サーバーが、自動フェールオーバーを開始するかどうかを決定できるようになります。 2 つのパートナーとは異なり、ミラーリング監視サーバーではデータベースの操作は行いません。 ミラーリング監視サーバーの唯一の役割は、自動フェールオーバーをサポートすることです。  
  
> [!NOTE]  
>  高パフォーマンス モードでは、ミラーリング監視サーバーによって可用性が低下する可能性があります。 データベース ミラーリング セッションでミラーリング監視サーバーを構成すると、プリンシパル サーバーは他のサーバー インスタンスの少なくとも 1 つに接続している必要があります。つまり、ミラー サーバーおよびミラーリング監視サーバーの両方またはいずれか一方と接続している必要があります。 どちらにも接続していないとデータベースが使用できなくなり、サービスの強制はできません (データが失われる損失の可能性あります)。 したがって、高パフォーマンス モードでは、ミラーリング監視サーバーを常に無効に設定しておくことを強くお勧めします。 高パフォーマンス モードに対するミラーリング監視サーバーの影響については、「 [データベース ミラーリングの動作モード](database-mirroring-operating-modes.md)」を参照してください。  
  
 次の図は、ミラーリング監視サーバーを使用した高い安全性モード セッションを示しています。  
  
 ![ミラーリング監視サーバーを使用したミラーリング セッション](../media/dbm-3-way-session-intro.gif "ミラーリング監視サーバーを使用したミラーリング セッション")  
  
 **このトピックの内容:**  
  
-   [複数のセッションでのミラーリング監視サーバーの使用](#InMultipleSessions)  
  
-   [ソフトウェアとハードウェアの推奨事項](#SwHwRecommendations)  
  
-   [自動フェールオーバーでのミラーリング監視サーバーの役割](#InAutoFo)  
  
-   [ミラーリング監視サーバーを追加または削除するには](#AddRemoveWitness)  
  
##  <a name="InMultipleSessions"></a>複数のセッションでのミラーリング監視サーバーの使用  
 特定のサーバー インスタンスは、それぞれ異なるデータベースに対応している同時実行データベース ミラーリング セッションで、ミラーリング監視サーバーとして機能することができます。 セッションが異なれば、異なるパートナーを含めることができます。 次の図は、ミラーリング監視サーバーが異なるパートナーを含む 2 つのデータベース ミラーリング セッションに参加しているサーバー インスタンスを示しています。  
  
 ![2 つのデータベース ミラーリングを監視するサーバー インスタンス](../media/dbm-witness-in-2-sessions.gif "2 つのデータベース ミラーリングを監視するサーバー インスタンス")  
  
 同じサーバー インスタンスを一部のセッションではミラーリング監視サーバーとして、他のセッションではパートナーとして、同時に使用することも可能です。 ただし実際には、ミラーリング監視サーバーまたはパートナーのどちらかとしてサーバー インスタンスを使用するのが普通です。 これは、パートナーには実稼働データベースを十分にサポートできるハードウェアを搭載した高度なコンピューターが必要であるのに対し、ミラーリング監視サーバーには [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]をサポートするものであればどのような Windows システムでも使用できるためです。  
  
##  <a name="SwHwRecommendations"></a>ソフトウェアとハードウェアの推奨事項  
 ミラーリング監視サーバーは、パートナーとは別のコンピューターに常駐させることを強くお勧めします。 データベース ミラーリング パートナーは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard Edition および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise Edition でのみサポートされます。 一方、ミラーリング監視サーバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Workgroup および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express でもサポートされます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]からアップグレードしている間を除き、ミラーリング セッション内のすべてのサーバー インスタンスでは、同じバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行している必要があります。 たとえば、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ミラーリング監視サーバーは、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ミラーリング構成からアップグレードする場合にサポートされますが、既存または新規の [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 以降のミラーリング構成には追加できません。  
  
 ミラーリング監視サーバーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のこれらのエディションのいずれかをサポートする任意の信頼性の高いコンピューター システムで実行できます。 ただし、実行中の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の Standard バージョンに必要な最小構成のサーバー インスタンスをミラーリング監視サーバーとして使用することをお勧めします。 これらの要件の詳細については、「 [SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」を参照してください。  
  
##  <a name="InAutoFo"></a>自動フェールオーバーでのミラーリング監視サーバーの役割  
 データベース ミラーリング セッションの間は、すべてのサーバー インスタンスが接続の状態を監視します。 パートナー間の相互接続が失われると、各パートナーはミラーリング監視サーバーを使用して、少なくとも 1 つのパートナーが現在データベースとして機能していることを確認します。 同期ミラー サーバーからプリンシパル サーバーへの接続が失われても、ミラーリング監視サーバーとの接続が失われていなければ、ミラー サーバーはミラーリング監視サーバーにアクセスして、ミラーリング監視サーバーとプリンシパル サーバーとの接続が失われたかどうかを判断します。  
  
-   プリンシパル サーバーとミラーリング監視サーバーとの接続が失われていなければ、自動フェールオーバーは行われません。 プリンシパル サーバーは引き続きデータベースとして機能し、パートナーから再接続されるときに、その間蓄積したログ レコードをミラー サーバーに送信します。  
  
-   プリンシパル サーバーからミラーリング監視サーバーへの接続も失われている場合、ミラー サーバーはプリンシパル データベースが使用できないことを認識します。 この場合、ミラー サーバーはすぐに自動フェールオーバーを開始します。  
  
-   ミラー サーバーからミラーリング監視サーバーおよびプリンシパル サーバーへの接続がどちらも失われた場合、プリンシパル サーバーがどのような状態であっても、自動フェールオーバーは行えません。  
  
 この少なくとも 2 つのサーバー インスタンスが接続されていなければならない要件を、 *クォーラム*と呼びます。 クォーラムでは、複数のパートナーが同時にデータベースとして機能することはないことが保証されます。 クォーラムの動作およびセッションに対するクォーラムの影響については、「 [クォーラム: データベースの可用性にミラーリング監視サーバーが与える影響 &#40;データベース ミラーリング&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)と呼ばれる 3 番目のサーバー インスタンスを配置する必要もあります。  
  
##  <a name="AddRemoveWitness"></a>ミラーリング監視サーバーを追加または削除するには  
 **ミラーリング監視サーバーを追加するには**  
  
-   [データベースミラーリング監視サーバーを追加または置き換える &#40;SQL Server Management Studio&#41;](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
-   [Windows 認証 &#40;使用してデータベースミラーリング監視サーバーを追加する Transact-sql&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
 **ミラーリング監視サーバーを削除するには**  
  
-   [データベースミラーリングセッションからミラーリング監視サーバーを削除 &#40;SQL Server&#41;](remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
## <a name="see-also"></a>参照  
 [データベースミラーリングセッション中の役割の交代 &#40;SQL Server&#41;](role-switching-during-a-database-mirroring-session-sql-server.md)   
 [データベースミラーリングの動作モード](database-mirroring-operating-modes.md)   
 [クォーラム: データベースの可用性 &#40;データベースミラーリングにミラーリング監視サーバーが与える影響&#41;](quorum-how-a-witness-affects-database-availability-database-mirroring.md)   
 [データベースミラーリング中に発生する可能性のあるエラー](possible-failures-during-database-mirroring.md)   
 [ミラーリングの状態 &#40;SQL Server&#41;](mirroring-states-sql-server.md)  
  
  
