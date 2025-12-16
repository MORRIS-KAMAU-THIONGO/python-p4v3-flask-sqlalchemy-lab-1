# yPlan: Implement Missing Flask Routes

## Information Gathered
From analyzing the test failures and codebase:

1. **Current State**: Flask app has only a root route `/` implemented
2. **Missing Routes**: 
   - `/earthquakes/<id>` - to retrieve specific earthquake by ID
   - `/earthquakes/magnitude/<magnitude>` - to retrieve earthquakes by magnitude
3. **Database**: SQLite with Earthquake model (id, magnitude, location, year)
4. **Seed Data**: 5 earthquakes with magnitudes ranging from 8.4 to 9.5

## Plan: Implement Missing Routes

### Route 1: `/earthquakes/<id>`
**File**: `server/app.py`
- Add GET route that accepts earthquake ID
- Query database for earthquake by ID
- Return 200 with JSON data if found (id, magnitude, location, year)
- Return 404 with error message if not found

### Route 2: `/earthquakes/magnitude/<magnitude>`
**File**: `server/app.py` 
- Add GET route that accepts magnitude value
- Query database for earthquakes matching that magnitude
- Return JSON with count and quakes list
- Return empty results if no matches found

## Dependent Files to Edit
- `server/app.py` - Add the two missing route implementations

## Followup Steps
1. Run tests to verify all routes work correctly
2. Confirm all 11 tests pass

## Test Expectations
- `/earthquakes/1` → 200 status with earthquake data
- `/earthquakes/999` → 404 status with error message  
- `/earthquakes/9.0` → 200 status with count=2, quakes list
- `/earthquakes/10.0` → 200 status with count=0, empty quakes list
