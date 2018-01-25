---
title: "パラメーターをコマンド |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-commands
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
caps.latest.revision: "40"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ba6fc1bec3061516f9a2657635696abec6f4d8b1
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="command-parameters"></a>コマンドのパラメーター
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  コマンド テキスト内のパラメーターは、疑問符文字でマークされます。 たとえば、次の SQL ステートメントでは 1 つの入力パラメーターがマークされています。  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 ネットワーク トラフィックを削減してパフォーマンスを向上させるために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは自動的に派生していませんパラメーター情報しない限り、 **icommandwithparameters::getparameterinfo**または**Icommandprepare::prepare**コマンドを実行する前に呼び出されます。 つまり、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが自動的にしません。  
  
-   指定されたデータ型が正しいことを確認してください**icommandwithparameters::setparameterinfo**です。  
  
-   アクセサー バインド情報で指定された DBTYPE から、そのパラメーターに対する適切な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型にマップすること。  
  
 アプリケーションで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型のパラメーターと互換性のないデータ型を指定すると、上記のいずれかが原因で、エラーが発生したり、有効桁数が失われる可能性があります。  
  
 このようなことが起きないようにするには、アプリケーションで次の条件を満たす必要があります。  
  
-   いることを確認*して*と一致する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ パラメーターの型の場合はハード コーディング**icommandwithparameters::setparameterinfo**です。  
  
-   アクセサーをハードコーディングしている場合、パラメーターにバインドされている DBTYPE 値の型を、パラメーターの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型と同じにします。  
  
-   アプリケーションのコードを呼び出す**icommandwithparameters::getparameterinfo**プロバイダーを取得できるように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パラメーターのデータ型に動的にします。 これにより、ネットワーク上でサーバーとの余分なやり取りが増えることに注意してください。  
  
> [!NOTE]  
>  プロバイダーには、呼び出すことはできません**icommandwithparameters::getparameterinfo**のいずれか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]UPDATE または DELETE ステートメントの FROM 句で指定を含むすべての SQL ステートメントのパラメーターを含むサブクエリに依存。SQL ステートメントのような比較の両方の式内のパラメーター マーカーを含むまたは定量化された述語です。または、クエリ関数のパラメーターをここでは、パラメーターのいずれか。 SQL ステートメントのバッチを処理するときに、プロバイダーも呼び出すことはできません**icommandwithparameters::getparameterinfo**バッチ内の最初のステートメントの後にあるステートメントのパラメーター マーカー。 コメント (/* \*/) では使用できません、[!INCLUDE[tsql](../../includes/tsql-md.md)]コマンド。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、SQL ステートメント コマンドの入力パラメーターをサポートしています。 プロシージャ呼び出しコマンドで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、入力、出力、および入力/出力パラメーターをサポートしています。 出力パラメーターの値は、実行時 (行セットが返されない場合のみ)、または返されたすべての行セットがアプリケーションによって使用されたときにアプリケーションに返されます。 返される値が有効であることを確認するを使用して**IMultipleResults**行セットの消費量を強制的にします。  
  
 ストアド プロシージャ パラメーターの名前を DBPARAMBINDINFO 構造体で指定する必要はありません。 値として NULL を使用して、 *pwszName*メンバーがあることを示す、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーがパラメーター名を無視してで指定された序数だけを使用する必要があります、 *rgParamOrdinals*のメンバー **icommandwithparameters::setparameterinfo**です。 コマンド テキストに名前付きのパラメーターと名前のないパラメーターの両方が含まれている場合、どの名前付きパラメーターよりも前に、名前のないパラメーターをすべて指定する必要があります。  
  
 ストアド プロシージャのパラメーターの名前が指定されている場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが有効であることを確認する名前を確認します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、コンシューマーから不適切なパラメーター名を受け取ると、エラーが返されます。  
  
> [!NOTE]  
>  サポートを公開する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]XML とユーザー定義型 (UDT)、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーを実装する新しい[ISSCommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)インターフェイスです。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
