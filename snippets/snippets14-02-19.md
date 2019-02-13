# To Do

* Create a class to model an Agent from the LITRealty App.
* Create the necessary views to:
   * Display all Agents.
   * Add a Agent (initially using a standard HTML form, but expanding it to use [Springs Tag Library](https://docs.spring.io/spring/docs/3.2.x/spring-framework-reference/html/view.html)
   * Delete an Agent
   * Edit an Agent.
* Create a Controller to handle client requests. 


# Useful code snippets for 14/02/2019  :eyes:

## Create a Agent Bean 
```
 public class Agent {
    
    private int id;
    private String name;
    private String fax;
    private String phone;
    private String email;
	
	//generate getters/setters and constructors
	//possibly override toString()
	
}

```
## AgentDB class (AgentDB.java)
import java.util.ArrayList;
import java.util.List;

public class AgentDB {

    
    static List<Agent> agentList = new ArrayList();
    
    static List<Agent> getAllAgents() {
        
        agentList.add(new Agent(1, "Sue Roberts", "999-555-111", "78-45-56-51", "Sue.Roberts@litrealty.com"));
        agentList.add(new Agent(2, "Natasha Watkins", "999-555-112", "78-45-56-52", "Natasha.Watkins@litrealty.com"));
        agentList.add(new Agent(3, "Chris Clarkson", "999-555-113", "78-45-56-53", "Chris.Clarkson@litrealty.com"));
        agentList.add(new Agent(4, "Laura Blain", "999-555-114", "78-45-56-54", "Laura.Blain@litrealty.com"));
        agentList.add(new Agent(5, "Dave Lindale", "999-555-115", "78-45-56-55", "Dave.Lindale@litrealty.com"));
        return agentList;
    }
    
    static void addAnAgent(Agent a) {
        agentList.add(a);
    }
    
    static void deleteAnAgent(int id) {
        Agent agentToRemove = null;
        for (Agent agent : agentList) {
            if (agent.getId() == id) {
                System.out.println("attempting to remove " + agent.getName());
              agentToRemove = agent;
            }
        }
        
        agentList.remove(agentToRemove);
    }
}
```

## JSP for displaying all agents (allAgents.jsp).
```
<%@ taglib uri = "http://java.sun.com/jsp/jstl/core" prefix = "c" %>
<%@page contentType="text/html" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <title>All Agents</title>
    </head>
    <body>
        <table style="width:100%">
            <tr>
             <th align="left">ID</th>
             <th align="left">Name</th>
             <th align="left">Fax</th>
             <th align="left">Phone</th>
             <th align="left">Email</th>
             <th align="left">Actions</th>
            </tr>
            <c:forEach items="${agentList}" var="agent"> 
                <tr>
                    <td>${agent.id}</td>
                    <td>${agent.name}</td>
                    <td>${agent.fax}</td>
                    <td>${agent.phone}</td>
                    <td>${agent.email}</td>
                    <td>
                        <a href="">Delete</a>
                        <a href="">Edit</a>
                        <a href="">Insert</a>
                    </td>
                   
                </tr>
            </c:forEach>
        </table>
    </body>
</html>
```

## 