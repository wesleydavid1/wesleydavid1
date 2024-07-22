def solution(queries):
    database = {}

    def process_query(query):
        operation = query[0]
        key = query[1]
        field = query[2]
        
        if operation == "SET":
            value = query[3]
            if key not in database:
                database[key] = {}
            database[key][field] = value
            return ""
        
        elif operation == "GET":
            if key in database and field in database[key]:
                return database[key][field]
            else:
                return ""
        
        elif operation == "DELETE":
            if key in database and field in database[key]:
                del database[key][field]
                return "true"
            else:
                return "false"

    results = []
    for query in queries:
        results.append(process_query(query))
    
    return results
