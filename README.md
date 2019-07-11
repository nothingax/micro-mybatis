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
    