# micro-mybatis
学习、 模仿mybatis的核心设计

## mybatis 的核心组件
### session
    1、数据源信息 -- configuration
    组件：sqlSessionFactoryBuilder
    是Configuration的builder 
    
    
    读取配置 -- 需要configReader，读取解析配置信息
    建立会话 -- new 即可
    
    sql-mapper文件读ResultSet取 -- xmlReader xmlParser
    mapper文件中的动态sql解析 -- sqlParser
        参数处理            -- ParameterHandler
        sql返回值处理  -- ResultSetHandler
    
    2、xml文档解析
        org.apache.ibatis.session.SqlSessionFactoryBuilder#build(java.io.Reader)
        构造XMLConfigBuilder 实例，即parser：
        1、 构造xpath 
        2、通过文件流获取Document
        （使用JDK api： Xpath、Document）
        
        解析节点 ：
        Xpath 以document为参数解析得到节点，逐级解析得到xml文档中的值。
        
        Mapper节点的解析：
        通过xnode获取xml的子node，得到mapper class路径，扫描路径中的 mapper接口class 。
        设置Configuration中的mapperRegistry： 添加mapper接口class到knownMappers。